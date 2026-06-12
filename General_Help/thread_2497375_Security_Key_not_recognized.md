---
title: "Security Key not recognized"
date: 2024-05-02
forum: General Help
---

### Post by oilhat on 2024-05-02
I am trying to get ubuntu to use a security key.  I would like to use it to authenticate to some of my online accounts.  I do not want my system to require a security key to login however.  It seems like I could end up with a locked system and I certainly want to avoid that.
 My security key is Thetis or Excel Security FIDO2.  Although it is not a genuine Yubikey, I thought I would try to use Yubikeys Manager for testing purposes.   Here is what I have done.

  ```
[FONT=monospace][COLOR=#000000]sudo apt install pcscd[/COLOR][/FONT]
```
INstall went fine.  I won't include all of the output here.
```
[FONT=monospace][COLOR=#000000]sudo apt-add-repository ppa:yubico/stable[/COLOR]
[/FONT]
```
Then
```
[FONT=monospace][COLOR=#000000]sudo apt install yubikey-manager[/COLOR]


[/FONT]
```

Then


```
[FONT=monospace][COLOR=#54ff54]**adam@OptiPlex-5050**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**/etc/udev/rules.d**[/COLOR][COLOR=#000000]$ systemctl status pcscd [/COLOR]
[COLOR=#54ff54]**&#9679;**[/COLOR][COLOR=#000000] pcscd.service - PC/SC Smart Card Daemon [/COLOR]
     Loaded: loaded (/lib/systemd/system/pcscd.service; indirect; vendor preset: enabled) 
     Active: [COLOR=#54ff54]**active (running)**[/COLOR][COLOR=#000000] since Thu 2024-05-02 13:26:47 CDT; 5s ago [/COLOR]
TriggeredBy: [COLOR=#54ff54]**&#9679;**[/COLOR][COLOR=#000000] pcscd.socket [/COLOR]
       Docs: man:pcscd(8) 
   Main PID: 20788 (pcscd) 
      Tasks: 3 (limit: 18864) 
     Memory: 672.0K 
        CPU: 7ms 
     CGroup: /system.slice/pcscd.service 
             &#9492;&#9472;20788 /usr/sbin/pcscd --foreground --auto-exit 

May 02 13:26:47 OptiPlex-5050 systemd[1]: Started PC/SC Smart Card Daemon.

[/FONT]
```

And finally
```
[FONT=monospace][COLOR=#54ff54]**adam@OptiPlex-5050**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**/etc/udev/rules.d**[/COLOR][COLOR=#000000]$ ykman info [/COLOR]
ERROR: No YubiKey detected!

[/FONT]
```

However, the device appears with lsusb as ExcelSecu FIDO2 Security Key
```
[FONT=monospace][COLOR=#54ff54]**adam@OptiPlex-5050**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**/etc/udev/rules.d**[/COLOR][COLOR=#000000]$ lsusb [/COLOR]
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub 
Bus 001 Device 003: ID 413c:2003 Dell Computer Corp. Keyboard SK-8115 
Bus 001 Device 002: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse 
Bus 001 Device 004: ID 1ea8:fc25 ExcelSecu FIDO2 Security Key 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

[/FONT]
```

What do I do next?  Keep in mind that I do not want to use the security key to log in to my system.

---

### Post by dragonfly41 on 2024-05-02
I can't help with any knowledge of Yubi (althugh I recognise that it is more widely used). I opted for Google Titan Key which I use as a 2FA option in accessing some services.

[https://cloud.google.com/blog/products/identity-security/titan-security-keys-now-available-on-the-google-store](https://cloud.google.com/blog/products/identity-security/titan-security-keys-now-available-on-the-google-store)

You might compare notes with this overview.

[https://support.google.com/accounts/answer/6103523](https://support.google.com/accounts/answer/6103523)

---

### Post by oilhat on 2024-05-03
I found another guide for the yubikey manager here.
[https://opensourceisfun.substack.com/p/installing-and-managing-the-yubikey](https://opensourceisfun.substack.com/p/installing-and-managing-the-yubikey)
One of the instructions is ```
                         sudo apt install opensc-pkcs11 libpam-pkcs11 pcscd
  
```

I have already installed pcscd above.  Can I install opensc-pkcs11 and libpam-pkcs11 without causing any major problems, such as rending myselfe

---

### Post by dragonfly41 on 2024-05-03
You can always uninstall/remove later. Perhaps use Synaptic Package Manager GUI.
```
sudo synaptic
``` to launch (if Synaptic is installed).
Search in Synaptic GUI "pcscd" for example.

"Middleware to access a smart card using PC/SC (daemon side)"
  
"The purpose of PC/SC Lite is to provide a Windows(R) SCard interface
in a very small form factor for communicating to smart cards and
smart cards readers."

But in Synaptic I see the other libraries to install. They seem safe to install.

"OpenSC provides a set of libraries and utilities to access smart
cards.  It mainly focuses on cards that support cryptographic
operations. It facilitates their use in security applications such as
mail encryption, authentication, and digital signature. OpenSC
implements the PKCS#11 API. Applications supporting this API, such as
Iceweasel and Icedove, can use it. OpenSC implements the PKCS#15
standard and aims to be compatible with all software that does so as
well."

---

### Post by oilhat on 2024-05-07
Dragonfly,  Thank you for the response.

So it sounds like you are saying yes, I can install these packages without causing any serious problems.  My concern is that I install some of these smart card packages and then I won't be able to log into my system.  From what I have read about smart cards, that is what they are for.

Is synaptic a gnome application?  I am using kde (kubuntu).  It has the Muon Package Manager.  I haven't used it before.  I tried it just now and I searched for pcscd like you did.  It seems to be similar.  

I think I will go ahead and install opens-pkcs11 and libpam-pkcs11.  If my thetis security key still doesn't work, maybe I will go and purchase a genuine yubikey.

---

### Post by dragonfly41 on 2024-05-07
Run ..
man synaptic

for reassurance.

---

### Post by dragonfly41 on 2024-05-07
Another find ...

[https://www.reddit.com/r/firefox/comments/untrya/u2f_keys_not_working_in_ubuntu_2204_remove_the/](https://www.reddit.com/r/firefox/comments/untrya/u2f_keys_not_working_in_ubuntu_2204_remove_the/)

---

### Post by currentshaft on 2024-05-07
ac

---

### Post by oilhat on 2024-05-13
Currentshaft.  Yes I have tried registering a security key.  Firefox displays a message to touch my security key to continue, but it doesn't work. I don't think firefox is recognizing the key.

So far, I have been reluctant to remove snap and install the deb.  I don't understand the process very well and I don't want to break anything.

I found another, more up to date post about installing the firefox deb and remove snap here.  [https://support.mozilla.org/en-US/questions/1412073](https://support.mozilla.org/en-US/questions/1412073)  [https://support.mozilla.org/en-US/questions/1412073](https://support.mozilla.org/en-US/questions/1412073)  or search for the title  **Firefox using FIDO2 security keys**.  I includes another FIDO2 test site [https://www.token2.com/tools/fido2-test/](https://www.token2.com/tools/fido2-test/)  which should be useful.  It seems to say that the issue has been resolved.  There is a further recommendation to disable apparmor.  So I tried it.

```
[FONT=monospace][COLOR=#54ff54]**OptiPlex-5050**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**/etc/udev/rules.d**[/COLOR][COLOR=#000000]$ systemctl stop apparmor [/COLOR]
[COLOR=#54ff54]**OptiPlex-5050**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**/etc/udev/rules.d**[/COLOR][COLOR=#000000]$ systemctl status apparmor [/COLOR]
&#9675; apparmor.service - Load AppArmor profiles 
     Loaded: loaded (/lib/systemd/system/apparmor.service; enabled; vendor preset: enabled) 
     Active: inactive (dead) since Mon 2024-05-13 08:19:38 CDT; 11s ago 
       Docs: man:apparmor(7) 
             https://gitlab.com/apparmor/apparmor/wikis/home/ 
    Process: 484 ExecStart=/lib/apparmor/apparmor.systemd reload (code=exited, status=0/SUCCESS) 
    Process: 10233 ExecStop=/bin/true (code=exited, status=0/SUCCESS) 
   Main PID: 484 (code=exited, status=0/SUCCESS) 
        CPU: 1ms 

May 13 06:06:59 OptiPlex-5050 systemd[1]: Starting Load AppArmor profiles... 
May 13 06:06:59 OptiPlex-5050 apparmor.systemd[484]: Restarting AppArmor 
May 13 06:06:59 OptiPlex-5050 apparmor.systemd[484]: Reloading AppArmor profiles 
May 13 06:06:59 OptiPlex-5050 apparmor.systemd[523]: Skipping profile in /etc/apparmor.d/disable: usr.sbin.rs[COLOR=#ffffff]>[/COLOR]
May 13 06:06:59 OptiPlex-5050 systemd[1]: Finished Load AppArmor profiles. 
May 13 08:19:38 OptiPlex-5050 systemd[1]: Stopping Load AppArmor profiles... 
May 13 08:19:38 OptiPlex-5050 systemd[1]: apparmor.service: Deactivated successfully. 
May 13 08:19:38 OptiPlex-5050 systemd[1]: Stopped Load AppArmor profiles.

[/FONT]
```

But that didn't work either.

Within the reddit post from dragonfly there is a link to get FIDO2 to work with snap.   [https://askubuntu.com/questions/1406921/allow-firefox-snap-access-to-usb-security-keys](https://askubuntu.com/questions/1406921/allow-firefox-snap-access-to-usb-security-keys)  It says the the manufacturer and product code need to be added to /etc/udev/rules.d/70-snap.firefox.rules

I checked on my system and it is in there already.

```
[FONT=monospace][COLOR=#000000]# Thetis U2F BT Fido2 Key [/COLOR]
SUBSYSTEM=="hidraw", KERNEL=="hidraw*", ATTRS{idVendor}=="1ea8", ATTRS{idProduct}=="fc25", TAG+="snap_firefox_
geckodriver"[/FONT]
```

So I haven't installed the debs yet.  It seems like it has been addressed withing snap and I'm just not willing to do install the debs right now.  Are there any other less invasive things that I can try?

---

### Post by currentshaft on 2024-05-13
3 2 1

---

### Post by dragonfly41 on 2024-05-14
The alternatives for 2FA are remote server EITHER sending an SMS one time password (OTP) OR requiring security key to be touched. You might try opening a test account with both options. Heroku is an example. I just touch Google key to be authorised. But the backup mode if key fails is SMS OTP.

---

### Post by oilhat on 2024-05-15
I found a partial solution. [https://support.mozilla.org/mk/questions/1404594](https://support.mozilla.org/mk/questions/1404594)    

So I shut down firefox, then restarted in safe mode from the command line.

```
[FONT=monospace][COLOR=#000000]firefox -safe-mode[/COLOR][/FONT]
```

Then I went to [https://www.token2.com/tools/fido2-test/](https://www.token2.com/tools/fido2-test/)  and tested my security key, and it worked.  I found the token2 test from the other firefox support post here.  [https://support.mozilla.org/en-US/questions/1412073](https://support.mozilla.org/en-US/questions/1412073)

There is further information in the first link above about getting the key to work by switching profiles.  I will try that later.

Dragonfly, your last post recommending opening a test account with Heroku.  Is that different or better than the token2 test utility that I tried above?

Does this explain anything?  Do you have any other ideas?  Perhaps I can get by with this work around or use chrome or something.  Thank you for your help.

---

### Post by dragonfly41 on 2024-05-15
[COLOR=#000000]> your last post recommending opening a test account with Heroku. Is that different or better than the token2 test utility that I tried above?
Not really .. it was just another rabbit I tried to pull out of a hat .. as often I do with wild ideas. i know that my security key works with Heroku (tried it yesterday) but it could be any other test regime[/COLOR]

---

