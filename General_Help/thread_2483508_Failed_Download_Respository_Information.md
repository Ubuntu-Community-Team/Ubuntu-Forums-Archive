---
title: "Failed Download Respository Information"
date: 2023-02-01
forum: General Help
---

### Post by daniell59 on 2023-02-01
The Title says it all.

I tried updating in the terminal. I am sorry to say that my knowledge is limited. 

aniel@daniel-P5Q-PRO:~$ sudo apt-get update
[sudo] password for daniel: 
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy InRelease
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates InRelease [114 kB]     
Hit:3 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                   
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-backports InRelease [99.8 kB]  
Get:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease [110 kB]      
Ign:6 [https://ppa.launchpadcontent.net/jconti/gnome3/ubuntu](https://ppa.launchpadcontent.net/jconti/gnome3/ubuntu) jammy InRelease    
Err:7 [https://ppa.launchpadcontent.net/jconti/gnome3/ubuntu](https://ppa.launchpadcontent.net/jconti/gnome3/ubuntu) jammy Release
  404  Not Found [IP: 185.125.190.52 443]
Reading package lists... Done                              
E: The repository 'https://ppa.launchpadcontent.net/jconti/gnome3/ubuntu jammy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

---

### Post by howefield on 2023-02-01
Looks like "Err:7 https://ppa.launchpadcontent.net/jconti/gnome3/ubuntu" has no jammy repository. Last supported release for that repository was Raring Ringtail, 13.04.

Remove or comment that line out from your sources.list.

You should be able to remove it using the Software Sources application.

---

### Post by daniell59 on 2023-02-01
> **howefield said:**
> Looks like "Err:7 https://ppa.launchpadcontent.net/jconti/gnome3/ubuntu" has no jammy repository. Last supported release for that repository was Raring Ringtail, 13.04.

Remove or comment that line out from your sources.list.

You should be able to remove it using the Software Sources application.

I do appreciate your help but I need more elaboration. As I previously stated, my knowledge is limited.

---

### Post by daniell59 on 2023-02-01
> **howefield said:**
> Looks like "Err:7 https://ppa.launchpadcontent.net/jconti/gnome3/ubuntu" has no jammy repository. Last supported release for that repository was Raring Ringtail, 13.04.

Remove or comment that line out from your sources.list.

You should be able to remove it using the Software Sources application.

I should have been more precise in my question. How do I remove that line from the source list.

---

### Post by howefield on 2023-02-01
I am not using Ubuntu at the moment, but open the Software & Updates application, should look similar to the attached image.

From the "Other Software" tab look for the offending line and uncheck it. then close, accept the prompt to reload your software sources.

---

### Post by daniell59 on 2023-02-01
> **howefield said:**
> Looks like "Err:7 https://ppa.launchpadcontent.net/jconti/gnome3/ubuntu" has no jammy repository. Last supported release for that repository was Raring Ringtail, 13.04.

Remove or comment that line out from your sources.list.

You should be able to remove it using the Software Sources application.

I did as you instructed. Should I try again to download the update?

---

### Post by howefield on 2023-02-01
Yes :)

---

### Post by daniell59 on 2023-02-01
> **howefield said:**
> Yes :)

All is well!

Thanks for your kind and informative assistance.

---

