---
title: "Whatsapp Web says my Chrome is not Chrome?"
date: 2015-01-22
forum: General Help
---

### Post by YTS_Chan on 2015-01-22
Whatsapp web is an exciting news recently. I got an android whatsapp and the web version works fine on Mac and Windows PC. However, when it comes to my Ubuntu PC at home, the webpage asked me to download Chrome ...... while I am already using Chrome to open the page.

One of my friend says that's because Ubuntu's Chrome is actually Chromium, but based on my understanding Chromium is the developing version of Chrome, while I am quite sure I am using a stable version that is not Chromium. That's just my understanding and I am not sure if it's correct..... So, is that the answer why I cannot use Whatsapp Web on Ubuntu or is that due to other reason?

P.S. On about page, Chrome says it is [COLOR=#303942][FONT=Ubuntu]Version 40.0.2214.91 (64-bit).[/FONT][/COLOR]

---

### Post by kerry_s on 2015-01-22
when does it tell you? i went there, i have the same chrome you have, it didn't say anything while i bounced around the site. i don't have an account so couldn't go much farther.

---

### Post by YTS_Chan on 2015-01-22
Thanks for helping. What I see is the same page as you see if you open the page in Firefox.

By the way, the url of the site is [http://web.whatsapp.com](http://web.whatsapp.com) , right?

---

### Post by vasa1 on 2015-01-22
I think you need the real Google Chrome for this. I have the latest Google Chrome (Version 40.0.2214.91 (64-bit)
) from Google and not from Canonical (which offers Chromium, not Chrome) and the latest WhatsApp and had no problem enabling the desktop version by scanning the QR code.

---

### Post by taberner-3107 on 2015-01-23
Same problem here. I downloaded my browser from google site (my version is 40.0.2214.91).

EDIT: Ok, I've just realized I have installed 32bits version... Reinstalling the correct version solve the problem.

---

### Post by Craig_Millar on 2015-01-30
> **YTS_Chan said:**
> Whatsapp web is an exciting news recently. I got an android whatsapp and the web version works fine on Mac and Windows PC. However, when it comes to my Ubuntu PC at home, the webpage asked me to download Chrome ...... while I am already using Chrome to open the page.

One of my friend says that's because Ubuntu's Chrome is actually Chromium, but based on my understanding Chromium is the developing version of Chrome, while I am quite sure I am using a stable version that is not Chromium. That's just my understanding and I am not sure if it's correct..... So, is that the answer why I cannot use Whatsapp Web on Ubuntu or is that due to other reason?

P.S. On about page, Chrome says it is [COLOR=#303942][FONT=Ubuntu]Version 40.0.2214.91 (64-bit).[/FONT][/COLOR]

It's down to the User-Agent string. Install this plugin: [https://chrome.google.com/webstore/detail/user-agent-switcher/ffhkkpnppgnfaobgihpdblnhmmbodake](https://chrome.google.com/webstore/detail/user-agent-switcher/ffhkkpnppgnfaobgihpdblnhmmbodake)

Then update the Chrome on Windows UA to, eg. Chrome 40:

[B]Mozilla/5.0 (Windows NT 6.1) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/41.0.2228.0 Safari/537.36
[/B]
Thereafter, change your UA to Chrome on Windows.

---

### Post by vasa1 on 2015-01-31
> **Craig_Millar said:**
> It's down to the User-Agent string. Install this plugin: ...
Then update the Chrome on **Windows** UA to, eg. Chrome 40:

[B]Mozilla/5.0 (Windows NT 6.1) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/41.0.2228.0 Safari/537.36
[/B]
Thereafter, change your UA to Chrome on **Windows**.
OP is using Ubuntu, not MS Windows.

---

### Post by manuel28 on 2015-02-27
Try using the latest version of Firefox.

---

### Post by slickymaster on 2015-02-27
> **vasa1 said:**
> I think you need the real Google Chrome for this. I have the latest Google Chrome (Version 40.0.2214.91 (64-bit)
) from Google and not from Canonical (which offers Chromium, not Chrome) and the latest WhatsApp and had no problem enabling the desktop version by scanning the QR code.
Same here. The only difference being that I'm on Chrome 40.0.2214.115 m (32-bit).

---

### Post by PreThunder on 2015-03-07
I built a chrome extension because I had the exact same problem. It's in the Web Store: [https://chrome.google.com/webstore/detail/web-whatsapp-chromium-fix/pgfmfnebbllpikciccdlbclochnangbi](https://chrome.google.com/webstore/detail/web-whatsapp-chromium-fix/pgfmfnebbllpikciccdlbclochnangbi)

I built it for Chromium but it should also work on Chrome for Linux in case web.whatsapp.com blocks that one as well

---

