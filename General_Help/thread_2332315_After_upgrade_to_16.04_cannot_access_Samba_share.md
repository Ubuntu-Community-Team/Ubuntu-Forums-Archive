---
title: "After upgrade to 16.04 cannot access Samba share"
date: 2016-07-30
forum: General Help
---

### Post by lou6 on 2016-07-30
I use Nautilus to access Western Digital My Cloud but after upgrading to 16.04 I can't connect. No error message, nothing happens.

I followed the advice found on askubuntu and added the line "client use spnego = no" to my smb.conf file at the top of the global section but no joy.

I also tried re-creating the nautilus bookmark using the ip address of the wdmycloud - no joy there either.

Can someone smarter than I (meaning almost everyone) help?

Thanks

EDIT: thinking the problem could be the deprecated nautilus in 16.04, I tried Thunar - same result, no access to samba share.

---

### Post by gordintoronto on 2016-07-30
You might also need this line:
client ntlmv2 auth = no

And a reboot never hurts.

---

### Post by lou6 on 2016-07-30
Thank you (I hope). I can't access the computer in question until tomorrow but I'll give it a try then. I saw the post in which what you suggest is mentioned but didn't see how that situation related to mine.

I'd like to understand how you arrived at your answer - is there something I can read to improve my knowledge base?

And yes, I do reboot whether I need it or not :)

---

### Post by lou6 on 2016-07-31
No, that did not help - tried both nautilus and thunar - neither can connect to samba share on wd mycloud.

I also tried gigolo but there is no access to windows shares or the default "workgroup" there either.

Checked launchpad - evidently this has been a known issue since late April.

---

### Post by lou6 on 2016-07-31
I've checked Launchpad and found that the bug referenced there was in Samba 4.3.9 

This is not my problem - the machine I am using does not have Samba installed - only smbclient and associated cifs packages. My problem also has nothing to do with paswords or no passwords.

Prior to the upgrade from 14.04 LTS to 16.04 LTS I was able to see my NAS (WD My Cloud) from Nautilus, Thunar or Gigolo - now I cannot access the device by any method.

I hope someone can help since I'm at a complete loss.

---

### Post by him610 on 2016-07-31
How about trying this; it always works for my fileserver...

From your file manager, click on *Connect to Server* then for the Server Address enter this,
```
 smb://ip_address_of_your_cloud
```

---

### Post by lou6 on 2016-08-01
That's how I've been connecting for the last several years, him610, but it no longer works since the upgrade to 16.04. As I mentioned above "I also tried re-creating the nautilus bookmark using the ip address of the wdmycloud - no joy there either."

What's really annoying about this is that another completely different method of connecting (Gigolo, which connects to remote filesystems via gvfs) no longer works either.

I'm at a loss here, folks. I'm not enough of a Linux expert to know what to try next and depending on the superior knowledge that I know is out there...

TIA for any help.

---

### Post by vs-ruthless on 2016-09-25
> **him610 said:**
> How about trying this; it always works for my fileserver...

From your file manager, click on *Connect to Server* then for the Server Address enter this,
```
 smb://ip_address_of_your_cloud
```

I'm having the same issue, cannot connect to a shared folder on another ubuntu pc on my lan. When I browse in the file manager it finds the workgroup ok, but times out when I try and connect.

The strange thing is all of my other pc's on the lan (windows & linux) have no issues connecting to that share folder except 16.04?

Just tried to connect **smb://ip_address** and is connects straight away no issues. So why does the above work and not the file browser?

Oh, one last thing when the pc firsts boots and I open the file manager, the network icon is missing. It does eventually appear, but I have to close it and reopen the file manager.

---

