---
title: "Remote Desktop Connection and RD Gateway"
date: 2015-01-04
forum: General Help
---

### Post by jduff on 2015-01-04
Hello, trying to find a way to connect to my Windows machine at work.

Looked for help with Remote Desktop Connection and RD Gateway but found nothing.

Anyone has a tip or guide that would be great.

Thanks for the help.

---

### Post by HermanAB on 2015-01-04
It is called rdesktop

---

### Post by PhilGil on 2015-01-04
I have been struggling with this myself for the last six months; here is my experience. The TL/DR version is that I've yet to find a way to get a working connection in Linux and am currently connecting using a Windows 7 virtual machine. That being said...

Freerdp is supposed to support RD gateway connections, but I've yet to connect for more than a minute or two without a crash. It is possible that our vendor is at fault (I use an RDP-connected virtual workstation at my office), but they will not work with me on their configuration since they don't support Linux. If you would like to try you'll want to install the latest version of freerdp from the remmina-next repository ([https://launchpad.net/~remmina-ppa-team/+archive/ubuntu/remmina-next](https://launchpad.net/~remmina-ppa-team/+archive/ubuntu/remmina-next)). After installing, open a terminal and try running the following command:
```
$ xfreerdp /v:*RDP server* /g:*gateway server* /u:*UserName* /d:*RDP Domain* /p:*Password*
```
The first time you do this you'll probably have to accept a certificate. If it doesn't work and you'd like to experiment, all the options are listed in the man pages for xfreerdp ```
$ man xfreerdp
``` or [here]("https://github.com/awakecoding/FreeRDP-Manuals/blob/master/User/FreeRDP-User-Manual.markdown").

I'll be following this thread with interest to see if you (or anyone else) is successful in getting a crash-free connection.

---

### Post by PhilGil on 2015-01-04
> **HermanAB said:**
> It is called rdesktopAs far as I know, rdesktop doesn't support RD Gateway.

---

### Post by PhilGil on 2015-02-07
If anyone is still following this thread...

Just received an update to freerdp this morning from the remmina-next repo. The new version is: 1.2.0~git20150207+dfsg-0utopic1.

Tested it this morning and was able to successfully connect via the gateway and maintain a stable connection for the 15 minutes or so I kept it open. Based on this I'm cautiously optimistic. On Monday I'll put it to the test and try using it for a full workday.

---

### Post by lazer_knezer on 2015-04-06
> **PhilGil said:**
> If anyone is still following this thread...

Just received an update to freerdp this morning from the remmina-next repo. The new version is: 1.2.0~git20150207+dfsg-0utopic1.

Tested it this morning and was able to successfully connect via the gateway and maintain a stable connection for the 15 minutes or so I kept it open. Based on this I'm cautiously optimistic. On Monday I'll put it to the test and try using it for a full workday.

Were you able to test this update out on a full day's worth of work? If so, how did the connection go? Thanks!

---

### Post by PhilGil on 2015-04-06
> **lazer_knezer said:**
> Were you able to test this update out on a full day's worth of work? If so, how did the connection go? Thanks!
Unfortunately not, I'm still unable to maintain a stable connection. My current experience is this (running the latest freerdp build from the remmina-next repo):

Office PC, Ubuntu 14.04, low bandwidth ethernet connection with many dropped packets:
Will not stay connected for more than a few minutes, bombs with error message "Failed to check FreeRDP file descriptor"

Home PC, Ubuntu 14.10, high bandwidth, low latency wireless connection:
Will stay connected for 15 to 30 minutes then bombs with error message "Failed to check FreeRDP file descriptor"

Bottom line is I still have to use a Windows virtual machine to connect. Sorry I don't have better news to report.

---

### Post by hargrave-a on 2015-11-09
> **PhilGil said:**
> After installing, open a terminal and try running the following command:
```
$ xfreerdp /v:*RDP server* /g:*gateway server* /u:*UserName* /d:*RDP Domain* /p:*Password*
```


Hi, I've been trying to setup a connection for my partner to connect in to her works RD server from our Ubuntu machine. What I came across was the exact above solution however it came up with a security protocol error along with a "destination path" error. The 2 questions I have ATM are:
- Does the /v flag require an fqdn? Or should logging in to the gateway with the /g /gu /gp flags direct me to the correct rd server on their local network?
- What could cause the security protocol error? I've tried forcing TLS/NLA/rdp/ext with the /sec flag and I'm using /ignore-cert as I believe certificate errors pop up when people use rdp to connect normally.

Those 2 questions *should* address the errors I get when attempting to connect. In the mean time, I guess I'll have to set up a Win7 VM for my partner...

---

### Post by PhilGil on 2015-11-09
> **hargrave-a said:**
> Hi, I've been trying to setup a connection for my partner to connect in to her works RD server from our Ubuntu machine. What I came across was the exact above solution however it came up with a security protocol error along with a "destination path" error. The 2 questions I have ATM are:
- Does the /v flag require an fqdn? Or should logging in to the gateway with the /g /gu /gp flags direct me to the correct rd server on their local network?
- What could cause the security protocol error? I've tried forcing TLS/NLA/rdp/ext with the /sec flag and I'm using /ignore-cert as I believe certificate errors pop up when people use rdp to connect normally.

Those 2 questions *should* address the errors I get when attempting to connect. In the mean time, I guess I'll have to set up a Win7 VM for my partner...

Before I try to help please understand that I am in no way an RDP expert, just an ordinary user trying to figure this stuff out.

The answer to your first question is, yes, I've always needed an fqdn (*server.domain.suffix*), but the remainder of your first question really depends on how the admin has set up the RDP connection.

In answer to your second question... I've never used the ignore-cert flag as I was asked to accept a cert during the initial login and haven't has a problem since.

**Some general, unsolicited, thoughts on freerdp's gateway support:**

RD gateway support is broken in the regular Ubuntu repository versions of freerdp, even in 15.10. The version I referenced in an earlier post (from the remmina-next repo) is also stale, dating back to February 2015. It may work for you. It was not production-ready for me.

I have been using nightly builds of freerdp from [this repo]("https://ci.freerdp.com/job/freerdp-nightly-binaries/") successfully for several weeks. It still crashes two or three times a day, but that is much improved over the February build. There has also been an on and off memory leak, but things seem to be slowly improving. Most days I'm able to use the nightlies for regular production.

For what it's worth, here is the script that I use to open my RDP session. When called from a terminal it opens a freerdp-nightly session and prompts for my RDP password (which is the same as my gateway password):

```

#! /bin/bash
# Read Password
echo -n Password: 
read -s password
# Run Command
/opt/freerdp-nightly/bin/xfreerdp /workarea -decorations /u:username /d:rdp-domain /p:$password +auto-reconnect +fonts +clipboard /a:drive,Desktop,path-to-desktop-on-host-system /v:rdp-server.domain.suffix /g:gateway-server.domain.suffix
```

TL/DR version: Things are much, much better than they were a few months ago, but don't get rid of your VM yet :)

---

### Post by hargrave-a on 2015-11-09
Thanks, that information should hopefully be very helpful. It's been a long time since I've used any Windows system, is it a safe bet that the domain suffix I'm logging on to would be .local?

---

### Post by PhilGil on 2015-11-10
> **hargrave-a said:**
> Thanks, that information should hopefully be very helpful. It's been a long time since I've used any Windows system, is it a safe bet that the domain suffix I'm logging on to would be .local?
Not sure what you mean. Your wife's work will have provided a domain and suffix for their RDP server (a .com, .edu. .org, or etc.). There may also be a separate domain for the gateway server.

---

### Post by hargrave-a on 2015-11-10
> **PhilGil said:**
> Not sure what you mean. Your wife's work will have provided a domain and suffix for their RDP server (a .com, .edu. .org, or etc.). There may also be a separate domain for the gateway server.

Nevermind. I didn't need the FQDN in the end. 

But thank you greatly, with your help for the new PPA, I've got it working a charm!

---

### Post by Nick_Wrathall on 2016-05-12
Hi,

I just stumbled across this discussion. I know it is a little old but just wanted to let you know how I set up my Remote Desktop Connection and RD Gateway using xfreerdp.

My platform is 14.04 32bit.
FreeRDP version is the standard repository version. I haven't bothered with the nightly builds because it seems stable enough for my requirements.

Install YAD from [URL="https://launchpad.net/~webupd8team/+archive/ubuntu/y-ppa-manager"]here
[/URL]
Create the following script in your home directory called ".sg.sh"

```
#!/bin/sh
frmdata=$(yad --title "Connect to remote computer" --form --field="Remote computer" --field="Username" --field="Password:H" --field="Domain" --field="Gateway")
frmcomputer=$(echo $frmdata | awk 'BEGIN {FS="|" } { print $1 }')
frmusername=$(echo $frmdata | awk 'BEGIN {FS="|" } { print $2 }')
frmpassword=$(echo $frmdata | awk 'BEGIN {FS="|" } { print $3 }')
frmdomain=$(echo $frmdata | awk 'BEGIN {FS="|" } { print $4 }')
frmgateway=$(echo $frmdata | awk 'BEGIN {FS="|" } { print $5 }')
xfreerdp /v:$frmcomputer /f /d:$frmdomain /u:$frmusername /g:$frmgateway /p:$frmpassword /cert-ignore
```

Create a new file in /usr/share/applications/ and call it rdpsg.desktop (I edited the original file for remmina), changing the Exec line from /home/<username>/.sg.sh to your home directory of course.

```
[Desktop Entry]
Version=1.0
Name=RDPSG
GenericName=Secure Remote Desktop Client
X-GNOME-FullName=Secure Gateway Remote Desktop Client
Comment=Connect to remote desktops
Exec=/home/<username>/.sg.sh
Icon=remmina
Terminal=false
Type=Application
Actions=
Categories=GTK;GNOME;X-GNOME-NetworkSettings;Network;
Actions=Profile;Tray;
Keywords=VNC;XDMCP;RDP;
X-Ubuntu-Gettext-Domain=remmina
```

This will allow you to run the connection from Dash. It also does not require the password to be in clear text in a script (this was my main concern with using FreeRDP in Bash).

[ATTACH=CONFIG]269018[/ATTACH]

[ATTACH=CONFIG]269019[/ATTACH]

If you require use of a custom port (other than 443) you can simply add the port to the Gateway address in much the same way as you would in MSTSC.exe. For instance we use 444 as our gateway port, so I insert<gateway>:444 in this field.

I hope this is helpful.

---

### Post by oldos2er on 2016-05-13
Old thread closed.

---

