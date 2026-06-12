---
title: "Replace/repair damaged package file"
date: 2016-02-10
forum: General Help
---

### Post by brian106 on 2016-02-10
I recently installed Ubuntu 15.10 on a mini laptop and also installed the Prey  tracking client. There were some problems during the Prey installation  and I tried editing the prey.postinst file but got confused and ended up  deleting all the content and saved it. So the file is now empty but is  still present in the related package. Consequently, updating does not  repair the damaged file. The Prey package is now installed and is  working fine but it niggles me that the repository now contains a  package that I know would not work if it was required in the future. I  am, therefore, assuming that I should delete either the file or the  whole package.
A search of the forum turned up the command:

 $ sudo apt-get --reinstall install prey

When I tried this, I got the response:

Reinstallation of prey is not possible, it cannot be downloaded.

Can anyone offer any alternative suggestions?

---

### Post by ian-weisser on 2016-02-10
How did you download and (almost) install prey the first time? Did you use a command? Did you follow some instructions?

What kinds of problems did you encounter while installing prey?

Was that the entire output of the apt-get command? Normally there is more.

---

### Post by brian106 on 2016-02-10
> **ian-weisser said:**
> How did you download and (almost) install prey the first time? Did you use a command? Did you follow some instructions?

I just went to the Ubuntu Software Centre, searched for Prey, selected it and clicked on 'Install'. Three times the install failed and then it appeared to install OK. However, Prey Panel could not find the device. I then went the the Prey website, selected Prey for Ubuntu/Debian and found I was redirected to the USC again. That displayed Prey as 'Installed'. When I check with Prey Panel again, it found the device.

> What kinds of problems did you encounter while installing prey? 
As above.

> Was that the entire output of the apt-get command? Normally there is more.

I entered the apt-get command as indicated and the response ended with the 'unable to download' statement but I didn't note what else it said.

Since I posted, I've also tried:

$ sudo apt-get remove prey 

and:

$ sudo apt-get install prey

However, the result is the same, i.e., the prey.postinst file is empty. I presume this is simply because the installation files, including the empty file, are already on the machine. Somehow, I need to delete and replace the whole package (assuming it is not possible to just delete and replace the empty file).
The Prey Panel is again unable to locate the device, despite the fact that the USC says Prey is installed.

---

### Post by ian-weisser on 2016-02-10
Fixing Prey so it reliably finds your device may be different from reinstalling Prey.
Are you sure you want to go down the reinstall path?

---

### Post by brian106 on 2016-02-10
Well, the final stroke the first time round was a command that I found in another thread:

$ sudo /usr/lib/prey/current/bin/prey config account setup

I've tried that again and it now says:

$ sudo /usr/lib/prey/current/bin/prey: command not found

I'm wondering if that command might be in the damaged prey.postinst file.

So, I'm not sure but maybe a package reinstall is the only option.

---

### Post by brian106 on 2016-02-10
Sigh of relief; I found the text of the empty file and was able to rewrite it. However, Prey Panel still cannot find the device.

---

### Post by brian106 on 2016-02-12
> **brian106 said:**
> Sigh of relief; I found the text of the empty  file and was able to rewrite it. However, Prey Panel still cannot find  the device.

For the benefit of anyone who might be interested, I have now found out why Prey could not identify the device.
In the process of uninstalling and reinstalling, the package reverted to v.0.6.2 whereas the current version is 1.5.0. Simply downloading and installing the current version reactivated the tracking process.
Why on earth is the old version still in the repository?

---

### Post by ian-weisser on 2016-02-12
> **brian106 said:**
> Why on earth is the old version still in the repository?

The Prey developers have not bothered to update the package in Debian, nor asked for the current version to be removed.

---

