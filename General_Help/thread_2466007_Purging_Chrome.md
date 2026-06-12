---
title: "Purging Chrome"
date: 2021-08-17
forum: General Help
---

### Post by makem2 on 2021-08-17
The command I used to purge chrome was:

```

 sudo apt-get purge google-chrome-stable

```

This command appeared to complete without error.

When I check if there is anything left in /home I find there is a google-chrome folder containing many files and folders in /home/makem/.config.

When I repeat the purge I get this result:

```

makem@XPS-13-9300:~$ sudo apt-get purge google-chrome-stable
[sudo] password for makem: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package google-chrome-stable
makem@XPS-13-9300:~$

```

When I use catfish file search for 'chrome' I see the list in /home/makem/.config which shows me that many of the chrome files are embedded in other programs such as steam and thunderbird.

Can I safely remove the google-chrome folder from ./home/makem/config?

---

### Post by &amp;KyT$0P# on 2021-08-17
> **makem2 said:**
> Can I safely remove the google-chrome folder from ./home/makem/config?

Yes.

[FONT=Courier New]sudo apt-get purge[/FONT] only uninstalls software from the system.  It does not delete user personal data for that software.

> many of the chrome files are embedded in other programs such as ... thunderbird.

[That "chrome" has nothing to do with Google Chrome]("https://flagfox.wordpress.com/2014/01/19/writing-restartless-addons/#step1") -
> no, this has nothing to do with the Google Chrome web browser. Google did something annoying and lazy when they wrote their browser: they didn&#8217;t bother to name it. The word &#8220;chrome&#8221; is an old technical term for the parts of a web browser other than the web page it is showing. The idea is that you have the web content on screen and then the bits around it: the &#8220;chrome&#8221;. (I didn&#8217;t make up the stupid jargon) Google naming their browser Chrome (upper-case &#8216;C&#8217;) was roughly equivalent to as if Ford were to name their next vehicle the Ford Car. 

---

### Post by deadflowr on 2021-08-17
Note that google-chrome also has a cache folder as well in ~/.cache.

---

### Post by makem2 on 2021-08-17
Thank you both

---

