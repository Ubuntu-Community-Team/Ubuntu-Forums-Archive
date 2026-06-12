---
title: "Opps! Something went wrong. Please refresh page"
date: 2022-02-10
forum: General Help
---

### Post by sofasurfer on 2022-02-10
Familysearch.org (the genealogy site) worked fine (using Firefox). But a couple of days ago I started getting this message on SOME of its pages but not all..."Opps! Something went wrong. Please refresh page". I would chalk this up to a defective website except that it works fine when I use Chromium. I updated and upgraded. I reinstalled Firefox from Synaptic. So, what could be my problem?

---

### Post by linux-sysop on 2022-02-10
I mostly use Chromium based browsers myself, currently running Vivaldi.  The key here is this one and only webpage is in question.  I think the most basic answer is, bad coding of a Javascript on their site.  You could install another Mozilla based browser, my favorite is SeaMonkey. 

I just opened the site on my Vivaldi in another tab, hit F12 and looked at console.  Even though the site loaded, I got a few 404 errors;

```

DevTools failed to load source map: Could not load content for https://www.familysearch.org/en/trustSection.css.map: HTTP error: status code 404, net::ERR_HTTP_RESPONSE_CODE_FAILURE
DevTools failed to load source map: Could not load content for https://www.familysearch.org/en/rootsTechPanel.css.map: HTTP error: status code 404, net::ERR_HTTP_RESPONSE_CODE_FAILURE
DevTools failed to load source map: Could not load content for https://www.familysearch.org/en/signUpSection.css.map: HTTP error: status code 404, net::ERR_HTTP_RESPONSE_CODE_FAILURE
DevTools failed to load source map: Could not load content for https://www.familysearch.org/en/liveGuidance.css.map: HTTP error: status code 404, net::ERR_HTTP_RESPONSE_CODE_FAILURE
DevTools failed to load source map: Could not load content for https://www.familysearch.org/en/nlihp.css.map: HTTP error: status code 404, net::ERR_HTTP_RESPONSE_CODE_FAILURE
DevTools failed to load source map: Could not load content for https://www.familysearch.org/en/hf2019footer-critical.css.map: HTTP error: status code 404, net::ERR_HTTP_RESPONSE_CODE_FAILURE
DevTools failed to load source map: Could not load content for https://www.familysearch.org/en/discovery.css.map: HTTP error: status code 404, net::ERR_HTTP_RESPONSE_CODE_FAILURE
DevTools failed to load source map: Could not load content for https://www.familysearch.org/en/initialDesign.css.map: HTTP error: status code 404, net::ERR_HTTP_RESPONSE_CODE_FAILURE
DevTools failed to load source map: Could not load content for https://www.familysearch.org/en/rootsTechBanner.css.map: HTTP error: status code 404, net::ERR_HTTP_RESPONSE_CODE_FAILURE
DevTools failed to load source map: Could not load content for https://www.familysearch.org/en/nlihpButton.css.map: HTTP error: status code 404, net::ERR_HTTP_RESPONSE_CODE_FAILURE
trycatch.js:153 GET https://www.familysearch.org/service/tree/ftuser/users/CURRENT 401

```

Nothing you can do about it, they need to repair the site.

---

