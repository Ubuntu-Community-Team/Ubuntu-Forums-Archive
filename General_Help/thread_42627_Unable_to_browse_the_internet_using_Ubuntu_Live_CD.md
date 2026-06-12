---
title: "Unable to browse the internet using Ubuntu Live CD."
date: 2005-06-18
forum: General Help
---

### Post by itxweather on 2005-06-18
Hi,

Can anyone advise why i'm unable to connect to the internet using a Live CD version of Ubuntu Linux?. I'm using a 3Com 802.11g PCCard and a D-Link D604-T Wireless Access Point/Ethernet Router and can connect to 192.168.1.1/ (no additional or third-party drivers have been loaded other than the ones that were automatically loaded upon installing the Ubuntu Linux Live CD).

I've managed to do a google search but cannot connect to any other web-sites ("Connection Refused" error message). 

Have configured SSID and WLAN connectivity seems to be working without any problems (WEP is not enabled).

Any suggestions would be greatly appreciated.
Thank you.

Best Regards.

---

### Post by Lorraine on 2005-06-24
Well, I don't know if this will help you at all, since you seem to be configured a bit differently from me, but I also initially had problems connecting to the internet using the Ubuntu Live CD.  In my case the problem was with Mozilla Firefox.  It has an IPv6 issue.  Don't ask me what that means, because I don't know.  Someone else told me that's what it was and told me to look up instructions to fix it.  I followed some instructions on the Unofficial Ubuntu Starter Guide [http://www.ubuntuguide.org/?#loadwebsitefasterfirefox](http://www.ubuntuguide.org/?#loadwebsitefasterfirefox), and I was up and surfing.  Just in case you've never changed any of the settings in about:config, all you do is double click on the filter that you are trying to change and it will go from false to true and vice versa.  Also, the maxrequest filter will open up a dialog box for you to change the default number when you double click it.  Also, if this does work for you, these are settings you'll have to change every time you boot up using the Live CD.

---

### Post by itxweather on 2005-06-26
[QUOTE=Lorraine]Well, I don't know if this will help you at all, since you seem to be configured a bit differently from me, but I also initially had problems connecting to the internet using the Ubuntu Live CD.  In my case the problem was with Mozilla Firefox.  It has an IPv6 issue.  Don't ask me what that means, because I don't know.  Someone else told me that's what it was and told me to look up instructions to fix it.  I followed some instructions on the Unofficial Ubuntu Starter Guide [http://www.ubuntuguide.org/?#loadwebsitefasterfirefox](http://www.ubuntuguide.org/?#loadwebsitefasterfirefox), and I was up and surfing.  Just in case you've never changed any of the settings in about:config, all you do is double click on the filter that you are trying to change and it will go from false to true and vice versa.  Also, the maxrequest filter will open up a dialog box for you to change the default number when you double click it.  Also, if this does work for you, these are settings you'll have to change every time you boot up using the Live CD.[/QUOTE]

Hi Lorraine,

Thank you for your reply. Have gone through the Firefox about:config settings and this appears to have fixed the problems i've been experiencing-a big thank you!.
Surfing the internet prior to making these changes was very problematic, some web-sites would load, some would not, most would result in a "permission or connection denied" or similar wording error. I've installed Ubuntu onto my PC now and am otherwise happy with the installation. One small problem i'm experiencing now though (with Firefox unfortunately), this being am unable to install missing plug-ins (they're needed for the weather banner at the top of my homepage). Clicking on the "Install Missing Plugins..." button does nothing :-(. Any ideas?.

Thank you once again.
Best Regards.

---

### Post by jesse on 2005-07-23
Which plugins does it say you need? 

Also, are you running the Ubuntu firefox package or at least one installed from a synaptic repository like debian, or did you download firefox from the mozilla web page and run their silly installation program from a terminal?

If you're running either the Ubuntu version or the debian version, then do the following to install various plugins. 

1. Launch synaptic package manager (open a root terminal and type synaptic)
2. Chose "repositories" from the "settings" menu at the top
3. Click on the "settings" button at the bottom of the new window that pops up and then make sure "show disabled sources" is checked at the top. 

4. Make sure "universe" and "multiuniverse" are checked and then click ok. 

5. Close synaptic

6. Edit the sources.list file (type "sudo gedit /etc/apt/sources.list" at a terminal)

7. Add the following lines to the file

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sarge main

(This is for Windows media and Quicktime codecs. Note that there are some legal questions about these which is why they are not included by default in Ubuntu)

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

(These are various updates and more)

deb [http://ftp.iasi.roedu.net/pub/mirrors/ftp.blackdown.org/java-linux/debian/](http://ftp.iasi.roedu.net/pub/mirrors/ftp.blackdown.org/java-linux/debian/) sarge non-free

(This is blackdown java, but this repository is sometimes down. If it doesn't work, you may need to try it later)

8. Save your new sources list and restart synaptic. 

9. Reload your package list and ignore the warnings about authentication and keys

10. Search for the following packages and select them for installation

flashplayer-mozilla
realplayer
j2re
acroread
mozilla-acroread
w32codecs

11. Click apply to install them
12. Open "repositories" from the settings menu, then uncheck the following

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sarge main

13. search for and install mplayer-k6. Make sure you're installing the Ubuntu version and not the "stable" or "sarge" version

Now your plugins should all work when you install firefox. Your /usr/lib/mozilla-firefox/plugins should look something like this

Index of file:///usr/lib/mozilla-firefox/plugins/
Up to higher level directory
File: flashplayer.xpt 	1 KB 	10/06/2004 	01:37:54 PM
File: libflashplayer.so 	2044 KB 	10/06/2004 	01:37:55 PM
File: libjavaplugin.so 	131 KB 	03/24/2005 	11:06:01 PM
File: mplayerplug-in.so 	196 KB 	04/04/2005 	10:42:15 AM
File: nphelix.so 	57 KB 	05/14/2005 	12:57:13 AM
File: nphelix.xpt 	5 KB 	05/14/2005 	12:57:13 AM
File: nppdf.so 	858 KB 	03/11/2005 	08:50:00 PM

Your /usr/lib/mozilla/plugins should look like this

Index of file:///usr/lib/mozilla/plugins/
Up to higher level directory
File: flashplayer.xpt 	1 KB 	10/06/2004 	01:37:54 PM
File: libflashplayer.so 	2044 KB 	10/06/2004 	01:37:55 PM
File: libjavaplugin.so 	131 KB 	03/24/2005 	11:06:01 PM
File: mplayerplug-in.so 	196 KB 	04/04/2005 	10:42:15 AM
File: nphelix.so 	57 KB 	05/14/2005 	12:57:13 AM
File: nphelix.xpt 	5 KB 	05/14/2005 	12:57:13 AM
File: nppdf.so 	858 KB 	03/11/2005 	08:50:00 PM

Note, the helix plugins (which are for real player) may not appear until you've run real player and selected "player reset" from the help menu to run the real player installation program.  :grin:

---

### Post by itxweather on 2005-07-24
Hello Jesse,

Many thanks for your very comprehensive reply. I can confirm that i've managed to successfully install Ubuntu Linux with the help of the community on ubuntuforums.org and am really impressed with this particular Linux distro. In order to offer some support to the Ubuntu Linux project i've bought clothing from their CafePress store.

One thing I am having problems with though is configuring Evolution Mail for sending e-mail via a v21mail.co.uk POP3 account. Probably down to the fact that the configuration is not correct.

Settings entered are as follows:

Server type: SMTP
Host: v21.co.uk 

smtp.v21.co.uk has also been entered in the Host field instead of v21.co.uk but doesn't work.

My isp account doesn't come with a POP3 account which is why I want to use "smtp.v21.co.uk" as this seems to work in other e-mail clients but I cannot get it to work in Evolution Mail.

Any suggestions would be appreciated.
Thank you.

Best Regards.

---

### Post by jesse on 2005-07-25
Hmm. So your isp doesn't have it's own smtp server address? You might want to ask them. If they do have one, you can use it (from your isp) as the outgoing mail server and your pop mail receiving server (not from your isp) as the incoming mail server. 

For example, when I used host.sk as my pop account, I used mail.host.sk as my incoming mail server and my isp Comcast's smtp address, smtp.comcast.net, as my outgoing server. 

I think you have to use the outgoing server of your isp regardless of who your pop provider is. 

If all else fails, there's always gmail from Google. I'll be happy to send you an invitation for a free account with over 2G of space.

---

### Post by damonw5 on 2005-07-25
[QUOTE=jesse]
7. Add the following lines to the file

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sarge main

(This is for Windows media and Quicktime codecs. Note that there are some legal questions about these which is why they are not included by default in Ubuntu)
[/QUOTE]

The Marillat repos are known to cause problems and are NOT recommended.  :|

---

### Post by jesse on 2005-07-26
What kinds of problems? I'm curious. 

I actually only temporarily enabled them to get a couple of harmless packages (like acroread) and then disabled them. I don't normally have them enabled.

---

