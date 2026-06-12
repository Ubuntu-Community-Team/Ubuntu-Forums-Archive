---
title: "The package needs to be reinstalled but I cant find an archive for it"
date: 2007-09-01
forum: General Help
---

### Post by GoldNugget on 2007-09-01
After installing the .deb packages for a Brother printer driver, I am getting this error:
The package hl1470nlpr needs to be reinstalled, but I can't find an archive for it.

I have tried the options suggested including:

sudo dpkg --remove --force-remove-reinstreq hl1470nlpr

Which gives the following message:

]dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 172142 files and directories currently installed.)
Removing hl1470nlpr ...
/var/lib/dpkg/info/hl1470nlpr.postrm: 3: /etc/init.d/lpd: not found
dpkg: error processing hl1470nlpr (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 hl1470nlpr[/B]

I have also used 
sudo apt-get remove --purge hl1470nlpr 

which gives the same message.

I have used: sudo dpkg --configure -a

which returns me to the command line without error or comment.

Attempting to reinstall the program give the following error:
The package may be corrupt, or you don't have permission. 

Synaptic is broken and wont update or upgrade. It lists 0 packages available or installed and returns this error:

E: The package hl1470nlpr needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

I am stuck here.  I may never get the printer to work, but I really need to get synaptic fixed. Thanks in advance.

---

### Post by orb9220 on 2007-09-01
> The package hl1470nlpr needs to be reinstalled, but I can't find an archive for it.

Where did you get the package from before? Was if from a site and you click the .deb and had gdebi package installer install it for you?

---

### Post by GoldNugget on 2007-09-01
The .deb packages came from Brother's website. It included the printer driver and the cupswrapper. I used the instructions on the website to install.  (here: [http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install5.html](http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install5.html)  )
 I did re-download the packages and check the permissions of the files.

---

### Post by stego_s_aurus on 2007-09-02
To manually abort the error so you can have a functioning package manager again (but with a bum package), Edit the /var/lib/dpkg/status file: Look for the entry that is giving you problems (search for the package name), and manually change the status from "install reinstreq half-installed" to "install ok installed". I know that this doesn't fix the problem with the package itself, but it at least gets the package manager out from being between a rock and a hard place.

In my case I had a package that wasn't working, I couldn't remove it, and I couldnt reinstall it either, so Apt was completely stuck. I found the problem with the program and manually fixed it to where the package was working again, so I did NOT want Apt or Synaptic or dpkg to do Anything with the package, but I could not find any way to Cancel the pending operation. Looking around, I found where someone mentioned editing the /var/lib/dpkg/status and removing the entry would help. in my case I just edited the file and changed the package status to "install ok installed".

---

### Post by GoldNugget on 2007-09-03
stego_s_aurus said: 

"To manually abort the error so you can have a functioning package manager again (but with a bum package), Edit the /var/lib/dpkg/status file: Look for the entry that is giving you problems (search for the package name), and manually change the status from "install reinstreq half-installed" to "install ok installed". I know that this doesn't fix the problem with the package itself, but it at least gets the package manager out from being between a rock and a hard place."

Your fix worked perfectly. Apt-get is repaired and downloading updates. Thank you so much for your response.

---

