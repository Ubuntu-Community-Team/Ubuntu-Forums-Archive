---
title: "Flash/HTML5 Help"
date: 2014-01-06
forum: General Help
---

### Post by Genkakuzai on 2014-01-06
[FONT=courier new]Hello Ubuntu Forums,

I'm running Xubuntu 13.10 [64-Bit] with XFCE 4.10 Desktop.

I use Firefox as my web browser, and when I first visited Youtube it asked me to install Flash. The automatic plugin finder popped up, tried to install flash through that but it failed. So I searched the add-ons and installed one that converted Flash to HTML5 and allowed me to watch videos.

Sometime today, videos stopped working. It will either display a please update your flash message otherwise tell me my web browser does not recognize any of the available video formats and provides a link for HTML5 Video FAQ.

I decided to uninstall the add-on, and open the terminal to run "sudo apt-get install flashplugin-installer"

It then tells me that I already have this installed, or so I believe?[/FONT]
[FONT=courier new]
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-installer is already the newest version.
The following packages were automatically installed and are no longer required:
  hyphen-en-us mythes-en-au openoffice.org-hyphenation
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```[/FONT]

[FONT=courier new]Any suggestions as to what I'm to do? I assumed the original sudo command I put in would install it but I still cannot play videos.[/FONT][FONT=courier new]

[/FONT]:shock:

[FONT=courier new]
[/FONT]

---

### Post by monkeybrain20122 on 2014-01-06
Install Ubuntu-restricted-extras (or xubuntu-restricted-extras?) from synaptic, that will install flash along with other multimedia codecs.

---

### Post by Genkakuzai on 2014-01-06
[FONT=courier new]Thank you for your response.

I opened Synaptic and installed the Xubuntu-Restrictive-Extras and there was another similar in name that it highlighted. Unfortunately, that did not allow me to play flash. But it did allow me to watch HTML5 videos. I know this because I searched for HTML5 Videos on YouTube and they played!

So, I decided to uninstall/reinstall flashplugin-installer. Not to my surprise, it did nothing!

Finally I reopened Synaptic and found "adobe-flashplugin" with description "Adobe Flash Player Plugin Version 11." I swear I searched for it before and it didn't show up. Regardless, I found it and installed it. 

Now Flash and HTML5 are playing without flaw.

Overall, I know the restrictive extras at least enabled HTML5 playback. During installation of Xubuntu, I decided to skip 3rd party software installation and I may have clicked that while flashplugin-installer was being downloaded or installed. Perhaps that did something, I don't know. 

But for anyone else with a similar problem with the flashplugin-installer, instead find "adobe-flashplugin" and you should be set!

Thanks again for response.
[/FONT]

---

### Post by mörgæs on 2014-01-06
Good, please mark the thread 'solved'.

---

