---
title: "Problems install gimp"
date: 2005-10-24
forum: General Help
---

### Post by Krmzn on 2005-10-24
Hi guys,

Need your support again. Im trying to install gimp (image editing tool). When I run ./configure, I get this error:

checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool

Am I missing a package? What packages should I apt-get?

Thanks!

Kristian

---

### Post by Suzan on 2005-10-24
But Gimp will be installed with the standard ubuntu-installation...?

If you haven't Gimp pre-installed, why don't you install it via apt/synaptic?

---

### Post by red_plague on 2005-10-24
sudo apt-get install gimp

---

### Post by nortonedd on 2005-11-28
I'm a very new Kubuntu user. If I'm trying to get gimp, it prompts me with: 
 
```

root@Voicu:/home/voicu # apt-get install gimp
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  gimp: Depends: gimp-data (= 2.2.8-2ubuntu1~hoary1) but it is not going to be installed
        Depends: libgimp2.0 (>= 2.2.0+rel) but it is not going to be installed
        Depends: libwmf0.2-7 (>= 0.2.8) but it is not going to be installed
  skype: Depends: libqt3c102-mt (>= 3:3.3.3.2) but 3:3.3.3-7ubuntu3 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@Voicu:/home/voicu # apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  skype
0 upgraded, 0 newly installed, 1 to remove and 163 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 9160kB disk space will be freed.
Do you want to continue [Y/n]?
```

But I don't want to REMOVE skype. Why is that needed? Could you please give me a solution to install gimp without uninstalling Skype. Thank you very much.

---

### Post by Paul Casey on 2005-11-28
[QUOTE=Suzan]But Gimp will be installed with the standard ubuntu-installation...?

If you haven't Gimp pre-installed, why don't you install it via apt/synaptic?[/QUOTE]


On Kubuntu 5.10 Gimp is not installed as default.  Also there is not Synaptic on Kubuntu...  it's the same but different package management gui tool called Adept (I think)..  But that should work to install Gimp.

---

