---
title: "Disable Firefox as default browser"
date: 2018-03-04
forum: General Help
---

### Post by zkab on 2018-03-04
I have Xubuntu 17.10 and Firefox 58.0.2 (both 64-bits).
Since I have installed Chrome I want to disable Firefox as my default browser and use Chrome as my default browser.
I have chosen Chrome in Preferred Applications and Chrome tells me that it is the default browser (settings) ... but Firefox tells me the same.
How do I disable Firebox as default browser since clicking on hyperlinks starts Firefox and not Chrome ...

---

### Post by kenogo2 on 2018-03-04
Strange... Which browser opens when you type ```
exo-open --launch WebBrowser
``` in the terminal? If it's Chrome, then you should be set! What issues are you encountering? Are links sometimes opened with firefox instead of Chrome? It's hard to help if you don't get a bit more specific :)

---

### Post by ajgreeny on 2018-03-04
If those hyperlinks are in emails in thunderbird it is the setting in t'bird that needs changing.

Go to **Preferences -> Atatchments - Incoming tab** and you can change the browser to open http, https.

---

### Post by zkab on 2018-03-04
exo-open --launch WebBrowser opens Chrome but the hyperlinks in TB opens Firefox.
Don't understand how to change in TB Preferences - Attachments - Incoming ... it looks like this in my case ... where do I add it should be Chrome

---

### Post by SuperFreak on 2018-03-04
TB   ___Edit in Menu>Preferences. Don't you just set Chrome as default in Preferences as shown in attachment (DuckDuckGo in my case)

---

### Post by zkab on 2018-03-04
I have Edit - Preferences - General ...
Default Search Engine: Bing, Yahoo, Amazon.con, Twitter Search, Wikipedia
Where should I set Chrome ?

---

### Post by SuperFreak on 2018-03-04
I think you have to install this addon [https://addons.mozilla.org/en-US/thunderbird/addon/google-search-for-thunderbi/](https://addons.mozilla.org/en-US/thunderbird/addon/google-search-for-thunderbi/)

---

### Post by zkab on 2018-03-04
Ok

---

### Post by zkab on 2018-03-05
Thanks for your support.

What I did was ...

1) Turned off TB and open ~/.thunderbird/<your_profile>/prefs.js.
Changed user_pref("mail.preferences.advanced.selectedTabIndex", 3); -> user_pref("mail.preferences.advanced.selectedTabIndex", 0);
2) Started TB
3) Now I got config editor in Pref -> Advanced
4) Followed guidelines in [http://kb.mozillazine.org/Changing_the_web_browser_invoked_by_Thunderbird](http://kb.mozillazine.org/Changing_the_web_browser_invoked_by_Thunderbird)
5) When I click at a hyperlink in TB it asks what browser should be used ... I specified Chrome ... and now it work

---

