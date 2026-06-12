---
title: "How to stop intruder popup on display"
date: 2023-03-07
forum: General Help
---

### Post by satimis on 2023-03-07
Hi all,

Following Intruder```

Best Forex Broker - Hong Kong
catchlucksuvery.top

```
frequently popup on display
(pls refer to screenshot attached)

Clicking its settings popup Google Settings

Default behaviour

```

Don't allow sites to send notifications
Features that need notifications won't work

```
Already checked.

Please advise how to check and stop it?

Thanks

Regards

---

### Post by BBQdave on 2023-03-07
A little information on your hardware, operating system and application (Google Chrome I presume) would be helpful... to be helpful :)

With limited information, I would suspicion that it is NOT Google Chrome, but another application or malware - trying to trick you to click into things.

In my years of using Google Chrome, on native Google hardware and Linux distros, I have never had pop-ups or malware from Google applications. Hopefully I did not just jinx myself :D

---

### Post by satimis on 2023-03-07
> **BBQdave said:**
> A little information on your hardware, operating system and application (Google Chrome I presume) would be helpful... to be helpful :)

With limited information, I would suspicion that it is NOT Google Chrome, but another application or malware - trying to trick you to click into things.

In my years of using Google Chrome, on native Google hardware and Linux distros, I have never had pop-ups or malware from Google applications. Hopefully I did not just jinx myself :D
Hi,

Thanks for your reply.

Performed following test;
1. Log out and re-log in Ubuntu 22.04
2. Only start Firefox browser.

The intruder disappears.  It is almost half hour.

Edit
==
I'll make another test, starting another SSD drive on this PC.  It is also running Ubuntu 22.04.  I'll start both Firefox and Google Chrome to see what will be the result.  I'll come back after the test

Regards

---

### Post by BBQdave on 2023-03-07
Again, just offering helpful guesses, but DuckDuckGo search engine is restrictive in giving your search information, and even has additional extensions to block pop-ups and targeted ads that are based on your searches. You might be receiving target ads, but it is suspicious that they are appearing as pop-ups.

---

### Post by satimis on 2023-03-07
> **BBQdave said:**
> Again, just offering helpful guesses, but DuckDuckGo search engine is restrictive in giving your search information, and even has additional extensions to block pop-ups and targeted ads that are based on your searches. You might be receiving target ads, but it is suspicious that they are appearing as pop-ups.
Start another SSD drive on this PC
Start Firefox
Start Google Chome

A popu starts on the display immediately.  Please see attached screenshot.  I just cancel it

Regards

---

### Post by coffeecat on 2023-03-07
@satimis, I think you might want to read these two pages:

[https://malwaretips.com/blogs/remove-catchlucksurvey-top/](https://malwaretips.com/blogs/remove-catchlucksurvey-top/)
[https://www.pcrisk.com/removal-guides/25176-catchlucksurvey-top-ads](https://www.pcrisk.com/removal-guides/25176-catchlucksurvey-top-ads)

The first mostly has directions for getting rid of this hijacker in Windows, but is nevertheless a useful read. That you've acquired a browser hijacker seems likely. That might be a useful avenue to explore.

---

### Post by satimis on 2023-03-07
> **coffeecat said:**
> @satimis, I think you might want to read these two pages:

[https://malwaretips.com/blogs/remove-catchlucksurvey-top/](https://malwaretips.com/blogs/remove-catchlucksurvey-top/)
[https://www.pcrisk.com/removal-guides/25176-catchlucksurvey-top-ads](https://www.pcrisk.com/removal-guides/25176-catchlucksurvey-top-ads)

The first mostly has directions for getting rid of this hijacker in Windows, but is nevertheless a useful read. That you've acquired a browser hijacker seems likely. That might be a useful avenue to explore.
Hi,

Thanks for your advice and links.

This SSD drive has been now running half an hour.  Both Firefox and Google Chrome are running.  No catchlucksurvey[.]top popup.

I suppose Google Chrome on another drive is infected.  I'll try to fix the problem later.  If still failure I'll re-install Google Chrome to see whether it can help.

Rgards

---

### Post by hakerdefo2 on 2023-03-07
Install uBlock Origin on Firefox,

[https://addons.mozilla.org/en-US/firefox/addon/ublock-origin/](https://addons.mozilla.org/en-US/firefox/addon/ublock-origin/)

Install uBlock Origin on Chrome,
[https://chrome.google.com/webstore/detail/ublock-origin/cjpalhdlnbpafiamejdnhcphjbkeiagm](https://chrome.google.com/webstore/detail/ublock-origin/cjpalhdlnbpafiamejdnhcphjbkeiagm)

And you should be fine, fingers crossed ;)

---

### Post by MAFoElffen on 2023-03-07
In "Google Chrome", check here:
Settings Icon > Settings > Privacy and security > Site Settings > Notifications...

Check these 3 settings:
 -- Default behavior
 -- Not allowed to send notifications
 -- Allowed to send notifications

And if you can't find where the culprit is there, then close down Chrome and then:
```

mv $HOME/.config/google-chrome/default $HOME/Documents/

```
Which will move your personal profile file out of there. Which when you restart Chrome, it will start and create a new profile file.

---

### Post by satimis on 2023-03-08
Hi all,

Lot of thanks for your advice.

Today I start the problematic Ubuntu 22.04 SSD, with only FireFox running (Google Chrome not stared).  Up-to-now, more than half an hour, no intruder pop up.

Then I follow MAFoElffen's advice on #9 performed following test;

Start google-chrome
-> Settings

Only "Default browser" there.  Pls refer to attached screenshot

I can't find ```

-- Default behavior
-- Not allowed to send notifications
-- Allowed to send notifications

```

Please advise.  Thanks

[B][COLOR="#FF0000"]Edit_1
===[/COLOR][/B]
Now .top intruder popup

pls refers to screenshot attached

Intruder continues popup.  Pls refer to further screenshot

[B][COLOR="#FF0000"]Edit-2
====[/COLOR][/B]

Performed following further test

1)
logout and re-login Ubuntu 22.04

2)
start only Firefox (without google-chrome)

3)
On Terminal
$ touch $HOME/.config/google-chrome/default $HOME/Documents/ intruder.txt

$ ls -al $HOME/.config/google-chrome/default $HOME/Documents/ > intruder.txt

Reading intruder.txt
No suspected files found.  All files are my past working documents


Regards

---

### Post by MAFoElffen on 2023-03-08
In Google Chrome Browser, the address line, go to
```

chrome://settings/content/notifications

```

---

### Post by satimis on 2023-03-08
> **MAFoElffen said:**
> In Google Chrome Browser, the address line, go to
```

chrome://settings/content/notifications

```
Thanks for your advice.

Performed following steps

On Google-Chrome browser run
chrome://settings/content/notifications

-> Allowed to send notification

[https://catchlucksurvey.top443](https://catchlucksurvey.top443)
click More
-> Remove

I'll perform;
Logout and re-login Ubuntu 22.04
Start Firefox and Google-Chrome

Continue watching whether .top would popup again

Regards

---

### Post by satimis on 2023-03-08
Hi MAFoElffen

I have been watching this problematic ubuntu 22.04 SSD for more than 4 hours.  No intruder popup again.

Thanks

Regards

---

