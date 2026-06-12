---
title: "Problems trying to install Brave browser - GPG key issues"
date: 2021-11-22
forum: General Help
---

### Post by GhX6GZMB on 2021-11-22
I'd like to try out the Brave browser, and from the (hopefully official) download page here:
[https://brave.com/linux/](https://brave.com/linux/)
I followed the instructions with no success. Here's the output:
```
macro@macro-pc:~$ sudo apt install apt-transport-https curl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
curl is already the newest version (7.68.0-1ubuntu2.7).
apt-transport-https is already the newest version (2.0.6).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
macro@macro-pc:~$ sudo curl -fsSLo /usr/share/keyrings/brave-browser-archive-keyring.gpg https://brave-browser-apt-release.s3.brave.com/brave-browser-archive-keyring.gpg
macro@macro-pc:~$ echo "deb [signed-by=/usr/share/keyrings/brave-browser-archive-keyring.gpg arch=amd64] https://brave-browser-apt-release.s3.brave.com/ stable main"|sudo tee /etc/apt/sources.list.d/brave-browser-release.list
deb [signed-by=/usr/share/keyrings/brave-browser-archive-keyring.gpg arch=amd64] https://brave-browser-apt-release.s3.brave.com/ stable main
macro@macro-pc:~$ sudo apt update
Get:1 https://brave-browser-apt-release.s3.brave.com stable InRelease [4.317 B]
Hit:2 http://ppa.launchpad.net/kicad/kicad-5.1-releases/ubuntu focal InRelease                                          
Hit:3 http://archive.ubuntu.com/ubuntu focal InRelease                                                                                      
Hit:4 http://archive.ubuntu.com/ubuntu focal-updates InRelease                                                                              
Hit:5 https://deb.opera.com/opera-stable stable InRelease                                                                       
Hit:6 http://archive.ubuntu.com/ubuntu focal-security InRelease     
Hit:7 http://ppa.launchpad.net/libreoffice/ppa/ubuntu focal InRelease
Hit:8 http://ppa.launchpad.net/ubuntuhandbook1/avidemux/ubuntu focal InRelease
Err:1 https://brave-browser-apt-release.s3.brave.com stable InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A8580BDC82D3DC6C
Reading package lists... Done
W: GPG error: https://brave-browser-apt-release.s3.brave.com stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A8580BDC82D3DC6C
E: The repository 'https://brave-browser-apt-release.s3.brave.com stable InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
macro@macro-pc:~$

```
As you see, it doesn't work, Brave apparently needs more than a running Lubuntu 20.04. The whole "public key" thing is outside my experience.

How can this be solved?

Thanks.

---

### Post by DuckHook on 2021-11-22
[list=1]
[*]You don't actually need *apt-transport-https*. The newest versions of apt have https transport built into it. Focal certainly does. No harm in installing it though.
[*]The point of this exercise is that you are trying to add Brave's repository to those of Canonical's so that henceforth, Ubuntu will treat the Brave repository as a trusted one, equal in every way to Canonical's. This is a potentially dangerous exercise and opens you up to possible MITM exploits. So, to safeguard you, people way smarter than me developed an encoding/verification technique called SSL. A "public key" is the public portion of a key pair needed for SSL encoding to ensure that your download has not been tampered with. It is very important and must be successfully installed before apt will permit a download from the Brave site.
[*]Your output indicates that you did not install this public key properly. Instead of using the line indicated in your link to the Brave site, try this: ```
curl -s https://brave-browser-apt-release.s3.brave.com/brave-core.asc | sudo apt-key --keyring /etc/apt/trusted.gpg.d/brave-browser-release.gpg add -
```&#8230;copy and paste this line if you can. As you likely know by now, Linux is prickly about accuracy. Example, that last "-" preceded by a space is very important; the command won't work without it.
[*]After successfully installing the public key, remember to do: ```
sudo apt update
```before you do: ```
sudo apt install brave-browser
```
[/list]

---

### Post by GhX6GZMB on 2021-11-23
Thank You for your reply. But I get the same result:
```
macro@macro-pc:~$ curl -s https://brave-browser-apt-release.s3.brave.com/brave-core.asc | sudo apt-key --keyring /etc/apt/trusted.gpg.d/brave-browser-release.gpg add -
[sudo] password for macro: 
OK
macro@macro-pc:~$ sudo apt update
Get:1 https://brave-browser-apt-release.s3.brave.com stable InRelease [4.317 B]
Hit:2 http://ppa.launchpad.net/kicad/kicad-5.1-releases/ubuntu focal InRelease                                                              
Hit:3 http://archive.ubuntu.com/ubuntu focal InRelease                                                                             
Get:4 http://archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]                                                          
Hit:5 http://ppa.launchpad.net/libreoffice/ppa/ubuntu focal InRelease                                                            
Err:1 https://brave-browser-apt-release.s3.brave.com stable InRelease                                               
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A8580BDC82D3DC6C
Hit:6 https://deb.opera.com/opera-stable stable InRelease                                                           
Hit:7 http://ppa.launchpad.net/ubuntuhandbook1/avidemux/ubuntu focal InRelease                                      
Get:8 http://archive.ubuntu.com/ubuntu focal-security InRelease [114 kB]                      
Get:9 http://archive.ubuntu.com/ubuntu focal-updates/main i386 Packages [563 kB]
Get:10 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages [1.345 kB]
Get:11 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 DEP-11 Metadata [278 kB]
Get:12 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 c-n-f Metadata [14,5 kB]
Get:13 http://archive.ubuntu.com/ubuntu focal-updates/universe i386 Packages [648 kB]
Get:14 http://archive.ubuntu.com/ubuntu focal-updates/universe amd64 Packages [876 kB]
Get:15 http://archive.ubuntu.com/ubuntu focal-updates/universe amd64 DEP-11 Metadata [357 kB]
Get:16 http://archive.ubuntu.com/ubuntu focal-updates/universe amd64 c-n-f Metadata [19,5 kB]
Get:17 http://archive.ubuntu.com/ubuntu focal-security/main i386 Packages [336 kB]
Get:18 http://archive.ubuntu.com/ubuntu focal-security/main amd64 Packages [1.024 kB]
Get:19 http://archive.ubuntu.com/ubuntu focal-security/main amd64 DEP-11 Metadata [35,7 kB]
Get:20 http://archive.ubuntu.com/ubuntu focal-security/main amd64 c-n-f Metadata [8.964 B]
Get:21 http://archive.ubuntu.com/ubuntu focal-security/universe i386 Packages [519 kB]
Get:22 http://archive.ubuntu.com/ubuntu focal-security/universe amd64 Packages [663 kB]
Get:23 http://archive.ubuntu.com/ubuntu focal-security/universe amd64 DEP-11 Metadata [64,7 kB]
Get:24 http://archive.ubuntu.com/ubuntu focal-security/universe amd64 c-n-f Metadata [12,9 kB]
Reading package lists... Done                                 
W: GPG error: https://brave-browser-apt-release.s3.brave.com stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A8580BDC82D3DC6C
E: The repository 'https://brave-browser-apt-release.s3.brave.com stable InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

I'm in over my head here. How difficult can it be to install a program?


!EDIT!: tried the M$ way (reboot). No cigar:
```
macro@macro-pc:~$ sudo apt update
[sudo] password for macro: 
Hit:1 http://ppa.launchpad.net/kicad/kicad-5.1-releases/ubuntu focal InRelease
Hit:2 http://archive.ubuntu.com/ubuntu focal InRelease                                                                                      
Hit:3 http://ppa.launchpad.net/libreoffice/ppa/ubuntu focal InRelease                                                                       
Hit:4 http://archive.ubuntu.com/ubuntu focal-updates InRelease                                                                              
Hit:5 https://deb.opera.com/opera-stable stable InRelease                                                                      
Hit:6 http://archive.ubuntu.com/ubuntu focal-security InRelease                                                                
Get:7 https://brave-browser-apt-release.s3.brave.com stable InRelease [4.317 B]
Hit:8 http://ppa.launchpad.net/ubuntuhandbook1/avidemux/ubuntu focal InRelease
Err:7 https://brave-browser-apt-release.s3.brave.com stable InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A8580BDC82D3DC6C
Reading package lists... Done
W: GPG error: https://brave-browser-apt-release.s3.brave.com stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A8580BDC82D3DC6C
E: The repository 'https://brave-browser-apt-release.s3.brave.com stable InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

---

### Post by ActionParsnip on 2021-11-23
```
 
curl -s https://brave-browser-apt-release.s3.brave.com/brave-core.asc | sudo apt-key add -

```

It's easy to install an application. Apt makes things very easy. You have added a 3rd party source and you need to sign it so that your package system trusts it. Alternatively you can edit the source file and add
```

[trusted=yes]

```
To the line. Online guides will help with the formatting. Then you don't need the key

---

### Post by GhX6GZMB on 2021-11-23
Thanks, but look, I'm just follwing the instructions from here: [https://brave.com/linux/#linux](https://brave.com/linux/#linux)

And it just doesn't work. It seems the key is invalid, not that I'm an idiot. The key file exists in /etc/apt/trusted.gpg.d/ after running one of the above curl commands.
I've tried deleting the key file and running the command again (resulting in a new key file). Still the same error.

---

### Post by GhX6GZMB on 2021-11-23
OK, I've now also removed brave.com from the "Software Sources","Other software" and tried again. No success. Something's wrong with the Brave key.

The browser may be good, I'd like to try it out, but this just makes me bawl in frustration.

---

### Post by DuckHook on 2021-11-23
Let's try a different approach. Instead of installing the key into /etc, let's install it into /usr
```
sudo curl -fsSLo /usr/share/keyrings/brave-browser-archive-keyring.gpg https://brave-browser-apt-release.s3.brave.com/brave-browser-archive-keyring.gpg
```
Then, add the repo:
```
echo "deb [signed-by=/usr/share/keyrings/brave-browser-archive-keyring.gpg arch=amd64] https://brave-browser-apt-release.s3.brave.com/ stable main"|sudo tee /etc/apt/sources.list.d/brave-browser-release.list
```
Then, to be absolutely sure, reboot to load whatever needs loading.
Then, update the repos and install.

---

### Post by GhX6GZMB on 2021-11-24
I see no point in installing in /usr/share instead of /etc/apt/trusted.gpg.d where all my other keys are.

I've given up on Brave. When this project is not even able to make a .deb package or supplying working keys, it's a waste of time to pursue it. What quality is the software then?

Thanks for your help.

---

### Post by ActionParsnip on 2021-11-24
The deb file is fine. Your system just needs to be told to trust the 3rd party source you added. Again, you can mark the repo as trusted in the source file. Nothing tricky

---

### Post by DuckHook on 2021-11-24
It's your call.

FWIW, I have had no problems installing this package in about a dozen computers by following nothing more than the steps listed in the Brave site. Nor, I suspect, did thousands of others. It's my favourite alternate browser to FF.

We don't know what other things you've done to your system. All modern OSes are highly complex beasts and earlier tweaks or config changes may have made your key installation problematic. It is unwise to jump to the conclusion that an app is substandard because you alone had issues installing it.

What I can tell you is that Brave is a treat. Having ads and tracking nerfed before they even load onto the page is not only liberating, but very advantageous from a security/privacy/anonymity/data-proprietorship perspective. I can get into pages that my heavily hardened FF won't load, yet have reasonable assurance that tracking has been reduced to a minimum.

But, to each, their own.

---

### Post by GhX6GZMB on 2021-11-24
> **ActionParsnip said:**
>  Again, you can mark the repo as trusted in the source file.

You've said this before. And I've no idea what it means. I'm NOT compiling Brave source code.

---

### Post by GhX6GZMB on 2021-11-24
Well, whaddyaknow.
Suddenly the key installtion worked in /etc as suggested in post #2.
I'm sure there was a key problem the last couple of days with Brave, as I haven't done anything differently. But we'll never know.
sudo apt update also works, but installation doesn't. Let's see if a reboot solves it.

EDIT:
Well a reboot didn't fix it, but I'm a bit further on. The key's installed, but:

```
macro@macro-pc:~$ sudo apt install brave-browser
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package brave-browser
```

Sigh...

---

### Post by GhX6GZMB on 2021-11-24
OK, final installment here, last hurdle conquered.

It works now. The key is installed in /etc/... and Brave works. The final problem was, that the "echo" command to update /etc/apt/sources.list.d was missing.

I'm still certain that brave.com/linux has had a key problem the last days. On my side, I've done everything the same way.

Thanks for your inputs.

---

### Post by dragonfly41 on 2021-11-24
Perhaps try Y PPA Manager next time to test keys. It is a handy tool.

---

### Post by T6&amp;sfpER35% on 2021-11-25
> I'm still certain that brave.com/linux has had a key problem the last days
iv'e installed brave (from their official site ,same as your's) a week ago ,and has done so couple times before , and never encountered a problem.

---

