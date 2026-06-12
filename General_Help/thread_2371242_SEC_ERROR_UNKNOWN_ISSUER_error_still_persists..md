---
title: "SEC_ERROR_UNKNOWN_ISSUER error still persists."
date: 2017-09-12
forum: General Help
---

### Post by pastor-t on 2017-09-12
Currently using Firefox 55.0.2 (64bit), and Ubuntu browser (with FF as default), and I am still getting the SEC_ERROR_UNKNOWN_ISSUER error on 3/4 of the websites I regularly visit.
At first, I thought it might have been FF, but tried visiting the same sites with the Ubuntu browser, and got the same problem... imagine the Ubuntu browser blocking Ubuntu.com :)

Tried all the fixes and patches suggested for FF, including re-installing, changing ssl3 settings, and killing off the cert8.db file, but still no joy. (Yes, a restart in between each).
 Anyone got any ideas?

--
Reverend Fuzzy

---

### Post by TheFu on 2017-09-12
Ubuntu doesn't make a browser.  All the programs in Ubuntu are made by small teams around the world, a few happen to be made by Canonical, but that isn't the majority on your system - or even close to the majority of programs.

Could other network security be blocking access to CAs on the internet?  AV seems to be a common issue and some corporate networks appear to block some CAs too.

[https://support.mozilla.org/en-US/kb/troubleshoot-SEC_ERROR_UNKNOWN_ISSUER](https://support.mozilla.org/en-US/kb/troubleshoot-SEC_ERROR_UNKNOWN_ISSUER)

Then there are the Ubuntu log files. What do they say? Anything helpful?

---

### Post by pastor-t on 2017-09-12
> **TheFu said:**
> Ubuntu doesn't make a browser. 

Then you tell ME what to call it ... I open it, the title says "Ubuntu Web Browser".
[IMG]http://www.msbministries.org/images/ss2.png[/IMG]

[https://support.mozilla.org/en-US/kb/troubleshoot-SEC_ERROR_UNKNOWN_ISSUER](https://support.mozilla.org/en-US/kb/troubleshoot-SEC_ERROR_UNKNOWN_ISSUER)

The issue is not antivirus related, as there is not yet an anti-virus utility installed.
(this is a new install)

> **TheFu said:**
> Then there are the Ubuntu log files. What do they say? Anything helpful?

Tell me where they are, and I'll tell you what they say.

x

---

### Post by vasa1 on 2017-09-12
> **pastor-t said:**
> ...
Tried all the fixes and patches suggested for FF, including re-installing, changing ssl3 settings, and killing off the cert8.db file, but still no joy. (Yes, a restart in between each).
 Anyone got any ideas?

--
Reverend Fuzzy
Have you tried running Firefox in safe mode or with a new profile without any extensions?

---

### Post by untrustytahr on 2017-09-12
Are you on some sort of corporate/business network that does intrusion detection at the perimeter possible intercepting the ssl traffic?

---

### Post by TheFu on 2017-09-12
> **pastor-t said:**
> Then you tell ME what to call it ... I open it, the title says "Ubuntu Web Browser".
[IMG]http://www.msbministries.org/images/ss2.png[/IMG]

[https://support.mozilla.org/en-US/kb/troubleshoot-SEC_ERROR_UNKNOWN_ISSUER](https://support.mozilla.org/en-US/kb/troubleshoot-SEC_ERROR_UNKNOWN_ISSUER)

The issue is not antivirus related, as there is not yet an anti-virus utility installed.
(this is a new install)

Tell me where they are, and I'll tell you what they say.

x

Help --> About to learn what browser is actually running. Or checking the process table using ps/top/htop would work too. 
This is a common issue with branded OSes trying to *make things simple*, but it just adds to confusion, IMHO.  Each flavor of Ubuntu could be using a different default browser.  Xubuntu, Lubuntu, Ubuntu-Desktop, Kubuntu, Ubuntu-Mate each come with different sets of programs, but the names in the menu system might be the same.
Also, the titles in the window borders are set by the window-manager, at the request of any process running with the current userid's credentials. That might be the program or it might not. The window-manager controls the border around all programs.  That is part of the X/Windows architecture. Colors, thickness, words, word placement (center, left, right, top), 

As for log files ... searching for "ubuntu log files" on the web found this: [https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)  There are a few other links from reputable sites at the top of the list I was given.  We all forget to check the log files, BTW.  There may be nothing in there - or it might explain exactly what is happening and why. No way to know without looking.  Almost all system processes write to log files (99.9999% of them), but desktop programs are hit or miss.

For desktop programs, if they are run from a terminal, they will often dump all sorts of information to the terminal which is helpful. There are almost always --debug options or -vv to get more verbose. More 'v's, like -vvvv, will sometimes give more detailed output.  According to the firefox manpage, the -jsconsole option will "Open  the Error console."  Whether that is helpful or not, I don't know.  There is also 'safe mode' - -safe-mode is the option.

Might try chromium, lynx, dillo, and opera browsers. Do they work for this issue or not?
Try creating a new userid and running FF under that account too.  
Each of these techniques will help to determine if it is only a FF issue or if it might be only for THIS userid OR if it is system-wide.

It is hard to know at what level to respond to the nice folks here looking for help for this type of question.  Too basic and people can be offended.  Too high level and things aren't clear to someone with less experience.  

Anyway, hope this is helpful.

---

### Post by pastor-t on 2017-09-12
> **vasa1 said:**
> Have you tried running Firefox in safe mode or with a new profile without any extensions?

Tried it ... no joy.

---

### Post by pastor-t on 2017-09-12
> **TheFu said:**
> 
Might try chromium, lynx, dillo, and opera browsers. Do they work for this issue or not?
Just tried Chromium, Lynx, and Dillo... when attempting to access ubuntu.com from each, the following results happened...

Chromium:
[IMG]http://www.msbministries.org/images/ss-chromium.png[/IMG]

Lynx:
[IMG]http://www.msbministries.org/images/ss-lynx.png[/IMG]

...and Dillo:
[IMG]http://www.msbministries.org/images/ss-dillo.png[/IMG]


Anyway, hope this is helpful.

Not a help, but thanks for trying.

x

---

### Post by pastor-t on 2017-09-13
> **untrustytahr said:**
> Are you on some sort of corporate/business network that does intrusion detection at the perimeter possible intercepting the ssl traffic?

No.

---

### Post by TheFu on 2017-09-13
Well, we know it isn't just firefox under the 1 userid.

> Try creating a new userid and running FF under that account too. 

What happened with that?

---

### Post by pastor-t on 2017-09-13
> **TheFu said:**
> Try creating a new userid and running FF under that account too.                       


What happened with that?

Tried it via guest account, as well as a fresh new admin account.
...still no joy.

---

### Post by TheFu on 2017-09-13
Any reason to think someone is doing a MiTM intercept with your traffic?  I'd check the traceroutes from the problem location, then some other internet place ... like a public library to the same place.  Do they mostly match?

---

### Post by pastor-t on 2017-09-15
> **TheFu said:**
> Any reason to think someone is doing a MiTM intercept with your traffic?  I'd check the traceroutes from the problem location, then some other internet place ... like a public library to the same place.  Do they mostly match?

No reason to believe my network would be interesting enough to someone to want to do that.
Never the less, I checked it ... a traceroute to Ubuntu.org from the problem location, and to the same url from another station on my network (Win7 x64) that is unaffected.
Aside from the starting hop IP, both traces are identical, all 30 hops.

---

