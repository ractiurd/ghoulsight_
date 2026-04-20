Ghoulsight XSS Scanner
======================

Ghoulsight is an advanced XSS vulnerability scanner designed for bug bounty hunters, penetration testers, and security researchers. It combines multiple scanning engines with browser-confirmed verification for zero false positive results.

Original Script: Nishan Fiyaz
Rebuilt & Upgraded: Mahedi Hasan (Ractiurd)


Installation
------------

Requirements:
- Go 1.21+
- Chrome/Chromium installed



Quick Start
-----------

    ghoulsight -u "https://target.com/search?q=test" -m r -file my_payloads.txt

    ghoulsight -raw request.txt -file my_payloads.txt

    cat urls.txt | ghoulsight -m r -file my_payloads.txt


Usage
-----

    ghoulsight -u <url> -m <mode> [options]
    ghoulsight -l <file> -m <mode> [options]
    ghoulsight --domain <domain> --depth 3 -m r,d,c
    ghoulsight --web --port 8080

TARGET:

    -u <url>              Single URL to scan
    -l <file>             URL list file
    -raw <file>           Load raw HTTP request from file
    --domain <domain>     Domain to crawl (auto-discovers URLs)
    stdin                 Pipe URLs via stdin

SCAN OPTIONS:

    -m <mode>             Scan mode(s): r, d, c, f (comma-sep, default: r)
    --file <path>         Custom payload file or folder
    -t <int>              Concurrent threads (default: 10)
    -T, --timeout <int>   Request timeout in seconds (default: 15)
    --depth <int>         Crawl depth (default: 2)
    -v, --verbose         Show detailed scan progress
    -o <file>             Save results to file
    -p, --probe           Probe URLs before scanning (default: true)
    --rc                  Reflection check only (no XSS testing)

NETWORK:

    --cookies <str>       Custom cookies (e.g., 'session=abc; token=xyz')
    -H <str>              Custom headers (e.g., 'Authorization: Bearer tok')
    --data <str>          Form data for POST scanning (e.g., 'user=test')

FUZZING:

    --fuzz-mode <mode>    Attack mode: single, cluster, pitchfork (default: single)
    --fuzz-replace <kw>   Custom FUZZ keyword (default: FUZZ)

WEB SERVER:

    --web                 Start web server interface
    --port <int>          Web server port (default: 8080)

SCAN MODES:

    r  reflected      Traditional reflected XSS (includes POST form scanning)
    d  dom            DOM-based XSS scanning
    c  context-aware  AI-powered context detection + payload generation
    f  fuzz           FUZZ keyword-based scanning (ffuf-style)


Trial Release
-------------

Ghoulsight is available as a FREE trial for everyone. Users can get up to 7 days of access and test their web applications for XSS vulnerabilities.

What's INCLUDED in the trial:

- Reflected XSS Scanner -- fast, parallel GET parameter testing
- POST Form XSS Scanner -- auto-extracts and tests HTML forms
- Raw Request Mode -- load Burp/ZAP exported requests directly (-raw)
- Store-then-Retrieve -- automatic PUT/PATCH/DELETE stored XSS detection
- Path-Based XSS Detection -- tests URL paths for injection points
- Smart Scan Mode -- stops after first confirmed XSS (saves time)
- FUZZ Mode -- cluster bomb, pitchfork, and single fuzzing with custom keywords
- Domain Crawling -- auto-discovers URLs from a target domain
- Custom Headers & Cookies -- full support for authenticated testing
- Custom Form Data -- POST scanning with your own parameter values
- URL List Scanning -- batch scan from file or stdin
- Reflection Check Mode -- filter URLs by reflection before deep scanning
- Multi-threaded scanning with configurable concurrency
- Custom XSS payload files (-file) -- bring YOUR own payloads
- Verbose mode for detailed scan insights

What's LOCKED (Premium Only):

- Context-Aware Scanner (-m c) -- intelligent, mutation-based payload generation
- DOM XSS Scanner (-m d) -- DOM-based vulnerability detection
- Web Server Mode (-web) -- browser-based dashboard interface

Trial Restrictions:

- Up to 7 days of access from activation date
- No built-in payloads -- users must provide their own XSS payload file (-file payloads.txt)
- Requires internet connection for trial validation
- Context-aware, DOM, and web server modes require a subscription password


Examples
--------

Scan a single URL with reflected mode:

    ghoulsight -u "https://example.com/page?id=1" -m r -file payloads.txt

Scan multiple URLs with verbose output:

    ghoulsight -l urls.txt -m r -file payloads.txt -v -o results.txt

Crawl a domain and scan all discovered URLs:

    ghoulsight --domain example.com --depth 3 -m r -file payloads.txt

Load a raw HTTP request from Burp/ZAP:

    ghoulsight -raw request.txt -file payloads.txt



Scan with custom cookies and headers:

    ghoulsight -u "https://target.com/page?q=test" -m r --cookies "session=abc" -H "Authorization: Bearer token"


Chrome Extension
----------------

The `extension/` directory contains a Chrome extension for Ghoulsight that allows you to collect cookies and headers from your browser and send URLs directly to the scanner.


License
-------

This project is licensed under the terms described in the LICENSE file.

#Ghoulsight #XSS #BugBounty #WebSecurity #InfoSec #CyberSecurity #Pentesting
