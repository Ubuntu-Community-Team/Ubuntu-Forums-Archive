---
title: "Klicking url opens firefox, but only with default webpage"
date: 2015-03-01
forum: General Help
---

### Post by martin-r on 2015-03-01
I installed XUBUNTU to resurrect an old IBM think pad X41. I am pretty happy with it except one strange issue:
After the fresh install klicking a URL in thunderbird opened firefox and loaded the respective URL. After a reboot and setting up firefox sync opening a http or https link just opens firefox with the default wegpage. The URL is not handed over anymore. 

I have read through the forums but did not find a solution. I browsed through the gconf-editor and found there were no url-handlers for ftp, http and https. I added ftp, http and https to gconf desktop/gnome/url-handlers and copied the key values from my other machine (Linux Mint). But it did not solve the problem.

Has anybody had a similar experience or even better a solution idea?

---

### Post by ajgreeny on 2015-03-01
Can you tell me which version of Firefox you have, I suspect FF36, as I have just noticed the same thing happening on my Xubuntu 14.04.2 using FF36 when I click on a link in an email.  All links opened at the url address prior to this using all versions up to and including FF35, so I believe this is a FF36 bug.

EDIT:-
I have now found a way to stop this happening.
The answer was at [http://askubuntu.com/questions/130158/how-do-i-make-thunderbird-open-links-in-chromium](http://askubuntu.com/questions/130158/how-do-i-make-thunderbird-open-links-in-chromium) with a few amendments to the details in the second answer and also renaming the mimeTypes.rdf file in your thunderbird profile as ~/.thunderbird/x#x#x#x#.default/mimeTypes.rdfbackup so a new one is made.

Any click on a link will now open a dialogue window and ask which application to use.  Ignore the default Web Browser if it is offered and use the "Choose" button and navigate to **/usr/bin/firefox**; you can repeat this and choose **/usr/bin/chromium-browser** if you wish and you will then get all three options (Web Browser, Firefox and Chromium-browser) when you click on a link.  If you choose **Web Browser** you will just go to the default browser's home page not the link you clicked on; if you choose either Firefox or Chromium-browser that browser will go to the link address.

EDIT 2:-
I am now finding exactly the same problem with hyperlinks in Libreoffice which have in the past taken me to the correct link in my default browser, Firefox when holding Ctrl, just as they should.  Now they just open FF to my default home-page and in spite of a search of LO preferences I can find no way to change this behaviour.

This makes me even more suspicious that it is a bug of FF 36, and it is **VERY ANNOYING**.

---

### Post by ajgreeny on 2015-03-02
Well even more strange happenings that I have come across, though maybe this has solved the problem for me, for now at least.

In my xfce Settings-manager -> Preferred Applications I have always changed the browser setting from Debian Sensible Browser to Firefox and this has never presented a problem to me, with links from TB and LO always opening properly to the correct address in Firefox.
With the upgrade to FF 36 this seems to have broken, with links opening FF as before but always to the homepage instead of the link I clicked.

As a test of all and everything possible I have just reset the Preferred browser back to Debian Sensible Browser, and the behaviour of both FF and LO has returned to what was expected with links again opening properly to the link address.

I will keep looking at this and search for any open bugs, but for me, at least, for the moment all is as it should be.

---

### Post by Elfy on 2015-03-02
possibly [lpbug]1425972[/lpbug]

Fixed here manually /usr/usr/share/xfce4/helpers/xfce4-firefox.desktop

commented last 2 lines - added bottom 2
```

##X-XFCE-Commands=%B -remote "openURL(about:blank,new-window)";%B;
##X-XFCE-CommandsWithParameter=%B -remote "openURL(%s)";%B "%s";
X-XFCE-Commands=%B;
X-XFCE-CommandsWithParameter=%B "%s";
```

---

### Post by ajgreeny on 2015-03-02
Thanks Elfy, I had found that bug and another duplicate for the same problem, [http://ubuntuforums.org/showthread.php?t=2267439&p=13237829#post13237829](http://ubuntuforums.org/showthread.php?t=2267439&p=13237829#post13237829) and I have added my comments to both.

I have also made the edit to the **/usr/share/xfce4/helpers/firefox.desktop** file suggested by George Shuklin and so far all appears to be going as it should.

---

### Post by martin-r on 2015-03-02
[**[COLOR=#000000]@ajgreeny[/COLOR]**]("http://ubuntuforums.org/member.php?u=27747")
yes, the firefox version is 36.0. 
Your proposal from post #3 fixed the URL problem in thunderbird. In the xfce Settings-manager -> Preferred Applications I just changed  the browser setting to Debian Sensible Browser. Now firefox loads links from thunderbird mails properly again. But this did not fix opening ULRs from a desktop link.

@[**[COLOR=#990303][B]Elfy**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=610428")
I have also applied the changes from your post #4 to the files
- /usr/usr/share/xfce4/helpers/xfce4-terminal.desktop and  
- /usr/share/xfce4/helpers/firefox.desktop
and this fixed also the desktop link issue! 
Now links from thunderbird and desktop links work again. This bug has cost me quite some hours over the weekend. Now I am really relieved that hunting it down is over!

Thanks to both of you for your support and troubleshooting!

---

### Post by eduard-budai on 2015-03-05
In Xubuntu 12.04.5 with xfdesktop 4.8.3-2ubuntu7 clicking links in pidgin 1:2.10.3-0ubuntu1.6 opens a Firefox new window with the homepage set in Firefox, although clicking links in e-mails in thunderbird 1:31.5.0+build1-0ubuntu0.12.04.1 opens the link in a new Firefox tab (normal/expected behavior).

My last lines in /usr/share/xfce4/helpers/firefox.desktop are:

X-XFCE-Binaries=firefox;firefox-gtk2;firefox-gtk;mozilla-firefox;
X-XFCE-Category=WebBrowser
X-XFCE-CommandsWithParameter=%B -new-tab "%s)";%B %s;

---

### Post by Lucas32 on 2015-03-05
i examined r/usr/share/xfce4/helpers/xfce4-terminal.desktop but i couldn't find the lines that Elfy commented out.
however, i did look at - /usr/share/xfce4/helpers/firefox.desktop and found the lines.  i commented those out and voila!

---

### Post by Elfy on 2015-03-06
> **Lucas32 said:**
> i examined r/usr/share/xfce4/helpers/xfce4-terminal.desktop but i couldn't find the lines that Elfy commented out.
however, i did look at - /usr/share/xfce4/helpers/firefox.desktop and found the lines.  i commented those out and voila!

oops - copy paste mistake, sorry ...

---

### Post by eduard-budai on 2015-03-10
After today's Firefox update to 36.0.1+build2-0ubuntu0.12.04.1 everything returned to normal: clicking any link in any program or window correctly opens the site indicated by the link in a new Firefox tab. 

My /usr/share/xfce4/helpers/firefox.desktop file remained unchanged (like in my previous post #7).

---

