---
title: "Internet SSL  Error in Ubuntu Only"
date: 2016-08-04
forum: General Help
---

### Post by dcb5739 on 2016-08-04
Getting a lot of SSL errors in google Chrome  on Ubuntu. 
Would not even let me log in to these forums. I have to boot into 
Windows to get here to look for some help
Removed all my extensions to start
Many popular sites such as espn.com and bing.com will not load at all,.
Been using 14.04 LTS for a few years with no real problem.
I did try the advanced options at boot up to run a few scans 
But it didnt make a difference
In Windows Vista every page loads normally, in Ubuntu right now 
not many load fully if at all
Laptop is wired connection to the router
Thanks in Advance
Dave

---

### Post by &amp;KyT$0P# on 2016-08-04
What if you reinstall the system certificates?
```
sudo apt-get --reinstall install ca-certificates
```

---

### Post by dcb5739 on 2016-08-04
Ill  give that a try

reinstall the system certificates has  made no change[COLOR=#000000][/COLOR]

---

### Post by &amp;KyT$0P# on 2016-08-04
Next step would be to see if other browsers are likewise affected.
Can you (at least temporarily) switch to Chromium?  First purge Chrome:
```
sudo apt-get purge google-chrome-stable
```
(replacing [FONT=Courier New]google-chrome-stable[/FONT] with the package name of your installed Chrome, if different)

Then try installing Chromium:
```
sudo apt-get install chromium-browser
```

If Chromium doesn't work either, can you please test a non-Chromium-based browser, such as [SeaMonkey]("http://www.seamonkey-project.org/")?

---

### Post by dcb5739 on 2016-08-04
Chrome Firefox and Chromium all the same issue will look into seamonkey

What does Purge Chrome do ?

---

### Post by &amp;KyT$0P# on 2016-08-04
> **dcb5739 said:**
> What does Purge Chrome do ?
Completely uninstalls Chrome including deleting all global configuration files (this doesn't include your user settings in your home folder).  Since Firefox and Chromium are likewise affected, no point in doing that :o

---

### Post by dcb5739 on 2016-08-04
I am at a loss here. It has worked so good for so long now

---

### Post by &amp;KyT$0P# on 2016-08-04
Is SeaMonkey affected or not?

If so, please post the exact contents of the cert error page it gives for ubuntuforums.org, including everything it says under "Technical details" (click to expand).

---

### Post by dcb5739 on 2016-08-05
How close is SeaMonkey To using Firefox
as this is what I get using Firefox
[FONT=arial]Secure Connection Failed[/FONT]

[FONT=arial]The connection to the server was reset while the page was loading.[/FONT]

[FONT=arial]    The page you are trying to view cannot be shown because the authenticity of the received data could not be verified.[/FONT]
[FONT=arial]    Please contact the website owners to inform them of this problem.

wasnt a box for tech details[/FONT]

---

### Post by dcb5739 on 2016-08-05
Downloaded SeaMonkey .. cant figure out how to install it

---

### Post by &amp;KyT$0P# on 2016-08-05
You don't install SeaMonkey, you just extract the tarball to your home directory (it extracts in its own subfolder called "seamonkey").  Then just run the seamonkey executable in there.

That's not a SSL error, that's a connection error.  Are you behind any firewall?

---

### Post by dcb5739 on 2016-08-05
Is there 1 in Ubuntu ?

---

### Post by dcb5739 on 2016-08-05
justt now I am using mint on a usb stick, Its from lst year, really thinking this problem started after a system update. I wanted to see if the older core file worked better
So far no errors

---

### Post by dcb5739 on 2016-08-05
Back into Ubuntu , disabled the UFW . ESPN and Bing will not load

---

### Post by &amp;KyT$0P# on 2016-08-05
> **dcb5739 said:**
> justt now I am using mint on a usb stick, Its from lst year, really thinking this problem started after a system update. I wanted to see if the older core file worked better
Maybe, but it's really hard to know what the core file(s) are in this case with the information we have right now.  Especially since Linux Mint is not Ubuntu.

> Back into Ubuntu , disabled the UFW . ESPN and Bing will not load
So are those now the only sites you can't access, or did it not help at all?

---

### Post by dcb5739 on 2016-08-05
No change in Chrome/Chromium, Firefox seems be loading all pages except Bing. Firefox always seemed slow in Ubuntu, Chrome was much faster.
Hard to play games in Facebook in Firefox always acts like its out of memory, which is why I preferred Chrome as it was much more responsive

---

### Post by &amp;KyT$0P# on 2016-08-05
I don't know what to make of that. :confused:

If you now clear the cache in Chrome or Chromium, does it load pages same as Firefox?

Maybe sniffing the packets will help diagnose this?  Problem is, I can't guess what we would be looking for, and it's a bad idea to upload the capture on the Internet given that it's very likely to contain private information.  I'll anyway out line the procedure for getting the capture log.  Someone else would be better able to suggest to you what to do with it.

Install Wireshark if you don't already have it:
```
sudo apt-get install wireshark
```

Get Chrome or Chromium ready to load an affected site, but don't do it just yet.

Then open Wireshark, select your network interface (or "any" if you don't know what your network interface is or don't see it), and start capture.

Now try to load an affected site, watch the error happen in the browser, then stop the capture.  You can optionally save the capture log with File > Save

---

### Post by dcb5739 on 2016-08-05
In Chrome, scrubbed the old profile and created a new one,  all but ESPN loads now. Works in Incognito mode though.
Wonder if i need to uninstall Chrome/Chromium and re install ?

---

### Post by dcb5739 on 2016-08-06
Looks like a corrupt profile was the culprit.
Thanks for all your help

---

### Post by &amp;KyT$0P# on 2016-08-06
You're welcome, glad it's working again.  :KS

---

