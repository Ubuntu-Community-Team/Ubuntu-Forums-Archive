---
title: "Problems with Chrome"
date: 2014-05-24
forum: General Help
---

### Post by DeMus on 2014-05-24
Hi,

This might not be the right forum to drop this problem but since it is a highly visited one I am hoping to get an answer here.
When I click on a link in, for example, a mail in Thunderbird the situation was that Chrome, which was open already, would get focus, open a new TAB and show me the correct webpage.
Now when I click a link, I see in the Chrome button on the taskbar that the new Tab is opened with the correct website, but Chrome stays in the background until I click the Chrome taskbar button.
What is the cause for this? What do I need to change to make the jump between Thunderbird and Chrome automatically again?
Who can help me? Need more info, please let me know and I supply it.
I do use Kubuntu 13.10, did not make the step yet.

---

### Post by DeMus on 2014-05-24
Nobody? Please help me solve this problem.

---

### Post by bapoumba on 2014-05-24
May be a Thunderbird setting. Not using it on this box so I cannot look for the correct setting : [https://support.mozilla.org/en-US/kb/hyperlinks-in-messages-not-working](https://support.mozilla.org/en-US/kb/hyperlinks-in-messages-not-working)
(Will set it up and look around).

---

### Post by DeMus on 2014-05-25
No, it's not a Thunderbird setting. Reason: it's not only happening with TB, but also with other programs. As I wrote I see the text in the Chrome taskbar button change because a new TAB is opened in Chrome, it's just that Chrome is not placed in the foreground on my screen. The link is transferred to Chrome, so TB and the other programs do their work. There must be a setting somewhere that prevents Chrome from taking focus.

---

### Post by bapoumba on 2014-05-25
Is chrome set up as your preferred browser ?

Please try to have the Chrome window not maximized : [https://code.google.com/p/chromium/issues/detail?id=45670](https://code.google.com/p/chromium/issues/detail?id=45670) comment #80 but does not seem to work for everyone. One user has written an extension to fix this ..

---

### Post by DeMus on 2014-05-25
Thank you bapoumba. Yes Chrome is my default browser. I did have it on full screen, now it is in window mode but the same happens. When I click a link in an e-mail, I see the name of the website in the Chrome taskbar button, in Chrome a new TAB has been added, but the program remains behind my e-mail program, or any other program in which I click on a link.
It used to be okay and I can not find out what caused this. I have no idea.

---

### Post by DeMus on 2014-05-25
Addition to last post: When Chrome is not open when I click a link the program is started and gets focus immediately. Then it all works like it should work.
When it is open already it does not.

---

### Post by bapoumba on 2014-05-25
You are welcome DeMus. I have found several Google threads about this, all directed at Windows users. This one had also Ubuntu users input. Will continue looking.

---

### Post by bapoumba on 2014-05-25
> **DeMus said:**
> Addition to last post: When Chrome is not open when I click a link the program is started and gets focus immediately. Then it all works like it should work.
When it is open already it does not.

Well, I have seen reports (on Windows) relating to this behavior : when users open Chrome from a Desktop shortcut, it gets focus. The second window opened with the same shortcut does not get focus either.

---

### Post by dragonfly41 on 2014-05-25
This rather old thread ...[https://productforums.google.com/forum/#!topic/chrome/EzCB8BXeDxQ](https://productforums.google.com/forum/#!topic/chrome/EzCB8BXeDxQ)

suggests not using the chrome window in maximized state.

---

### Post by bapoumba on 2014-05-25
You know what ?
I have configured Sylpheed (using lubuntu here) rather than installing TB. As I am testing Firefox for now, this is my current system preferred browser. I have the same behavior. Clicking a link (for ex from a notification mail for a forums new post in a subscribed thread) does not give focus to FF..

In sylpheedrc, I have this uri_open_command=sensible-browser '%s'
May be that is the common behavior ? Now will have a look at if and how it can be changed.

---

### Post by DeMus on 2014-05-25
Thing is, also in non maximized state the program does not get focus and stays in the background.

---

### Post by bapoumba on 2014-05-31
Just ran into something. As my screen is 13", which I consider being small, I usually open the mail reader in one desktop and the browser in another one. This morning I opened both on the same desktop, don't ask me why.. If I click on a link in Sylpheed (my mail reader), it opens the link in the browser (Firefox) and the browser gets focus. So my question is : would you be using TB and Chrome on two different desktops, and if so, would you please try having them both on the same ?
Thanks :)

Edit : I did not think of this, as on Mac OS, the browser gets focus even if on a different desktop..

---

### Post by DeMus on 2014-05-31
Thank you for still trying to find an answer for my problem. In the mean time I did the following:
I did a clean install of Kubuntu 14.04 and I really mean clean, no config files remained so I had to config everything by hand as if it was the first time I installed a Linux distro. Did not make any change.
I then copied my Google-chrome folder from the back-up to the .config folder in my home area to have "my" chrome back, still no changes of course.
I now wonder if it is a Chrome issue or an OS issue.

I have Thunderbird and Chrome on the same desktop so can't change anything there.

I will make Firefox the default webbrowser just to test it. Hole on, be right back.
Well, with FF being the default browser it works as it should: a new TAB is created and FF is shown this TAB. So it must be Chrome after all.

Thanks again. Will continue trying this and that.

---

### Post by bapoumba on 2014-05-31
Well, there is one thing.

In Firefox about:config shows one option browser.autofocus;true. I cannot find any equivalent in chrome://flags for ex.
There are dozens of bug reports on Chrome when you broaden the search and do not limit to mail clients..

---

### Post by DeMus on 2014-06-01
Hello again,

In the mean time I installed Mint 17 Cinnamon-64bits and there it works like it should work. Thing is I don't like the Cinnamon interface since it is so dull. Everything is grey, static and not configurable like in KDE. So I switched back to Kubuntu and now I have the same problem again. Strange thing is: it used to be good until one moment I noticed the webbrowser does not get focus when I click on a link in "doesn't matter which program". I guess it is some kind of update which causes this.
In about one month Mint will have finished the MintKDE 17 edition and I will have another look.
For now thank you very much for all the help you gave me.

---

### Post by bapoumba on 2014-06-01
You are most welcome :)

I guess the question is now : is this a browser-specific setting or a desktop environment setting for Chrome.
May be you could compare the two on both distributions, but I'm not sure where to start looking..

---

