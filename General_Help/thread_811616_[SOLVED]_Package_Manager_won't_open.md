---
title: "[SOLVED] Package Manager won't open"
date: 2008-05-29
forum: General Help
---

### Post by rogerzoom on 2008-05-29
Help please!
I am new to Ubuntu and in trying to install Skye I must have made an error because I am now unable to open my package installer. I get this message:-

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

How do I reload?

What to do?

help!

---

### Post by WRDN on 2008-05-29
If Synaptic is broken, you could try reinstalling it, using the following command from the terminal:

> sudo apt-get install --reinstall synaptic

---

### Post by rogerzoom on 2008-05-29
Thanks, unfortunately when I tried to reinstall synaptic I got this-

E:Type '--14:31:46--' is not known on line 1 in source list /etc/apt/sources.list.d.medibuntu.list
E:The list of sources could not be read.

Any ideas?

---

### Post by Seisen on 2008-05-29
Post your source list

```
cat /etc/apt/sources.list
```

---

### Post by drs305 on 2008-05-29
See my post #19 for an easy way to solve this if it's a corrupted medibuntu.list file !

Your sources list references what probably is a corrupt medibuntu file. You need to open medibuntu.list and correct the error. You can fix it or bypass it by deselecting the medibuntu repository in the synaptic list. To correct it:

Backup and edit:
```

sudo cp /etc/apt/sources.list.d/medibuntu.list /etc/apt/sources.list.d/medibuntu.list-`date +%F`
gksudo gedit /etc/apt/sources.list.d/medibuntu.list

```

This should be the entire contents of the file. If you have anything else, delete it all and replace it with:
```

## Medibuntu - Ubuntu 8.04 LTS "hardy heron"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ hardy free non-free
deb-src http://packages.medibuntu.org/ hardy free non-free

```

---

### Post by FuturePilot on 2008-05-29
> **drs305 said:**
> Your sources list references what probably is a corrupt medibuntu file. You need to open medibuntu.list and correct the error. You can fix it or bypass it by deselecting the medibuntu repository in the synaptic list. To correct it:

Backup and edit:
```

sudo cp /etc/apt/sources.list.d/medibuntu.list /etc/apt/sources.list.d/medibuntu.list-`date +%F`
gksudo gedit /etc/apt/sources.list.d/medibuntu.list

```

This should be the entire contents of the file. If you have anything else, delete it all and replace it with:
```

## Medibuntu - Ubuntu 8.04 LTS "hardy heron"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
# deb http://packages.medibuntu.org/ hardy free non-free
# deb-src http://packages.medibuntu.org/ hardy free non-free

```

Make sure to uncomment the sources or else they are useless.
Make them look like.
```
## Medibuntu - Ubuntu 8.04 LTS "hardy heron"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ hardy free non-free
deb-src http://packages.medibuntu.org/ hardy free non-free
```
Then run 
```
sudo apt-get update
```

---

### Post by rogerzoom on 2008-05-29
Thanks. I tried this
> sudo cp /etc/apt/sources.list.d/medibuntu.list /etc/apt/sources.list.d/medibuntu.list-`date +%F`
gksudo gedit /etc/apt/sources.list.d/medibuntu.list

But got the reply
> cp: target '/etc/apt/sources.list.d/medibuntu.list' is not a directory

Any ideas?

---

### Post by drs305 on 2008-05-29
If you didn't cut & paste, you may have used the wrong apostrophe symbol,had an extra space or I mistyped it. In any case, open the file (if it exists) and see what it contains. Replace the contents if it contains anything but the four lines I listed.

You can see if the medibuntu file exists with:
```
ls /etc/apt/sources.list.d
```

---

### Post by rogerzoom on 2008-05-29
Okay cool, I think I'm getting it. How do I open the medibuntu file?

---

### Post by drs305 on 2008-05-29
> **rogerzoom said:**
> Okay cool, I think I'm getting it. How do I open the medibuntu file?

```
gksudo gedit /etc/apt/sources.list.d/medibuntu.list
```

What we are doing is trying to repair your medibuntu repository listing. If you want or need to get things working without repairing the problem, you can just go to synaptic, Settings, Repositories and deselect medibuntu. That should restore the remaining repositories (but won't correct the error should you enable medibuntu again).

---

### Post by rogerzoom on 2008-05-29
Still no joy. How do I deselect medibuntu?

---

### Post by FuturePilot on 2008-05-29
Is it not opening? Are you getting any errors when you run that command?

---

### Post by rogerzoom on 2008-05-29
I am unable to open synaptic. Wont let me - a window pops up saying
> E: Type '--14:31:46--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.


When I open the medibuntu list I see this
> --14:31:46--  [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list)
           => `feisty.list.1'
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.10
Connecting to [www.medibuntu.org|87.98.242.10|:80](www.medibuntu.org|87.98.242.10|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 224 [text/plain]

    0K                                                       100%   12.11 MB/s

14:31:47 (12.11 MB/s) - `feisty.list.1' saved [224/224]

Thanks for bearing with me ...

---

### Post by drs305 on 2008-05-29
> **rogerzoom said:**
> Still no joy. How do I deselect medibuntu?
Click on the System icon, then Administration, Synaptic Package Manager. Then select Settings, Repositories, Third Party Software and deselect any listing with medibuntu in it. Then 'Reload'.

---

### Post by FuturePilot on 2008-05-29
> **rogerzoom said:**
> 


When I open the medibuntu list I see this



Delete everything in that file and replace it with
```
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ feisty free non-free
deb-src http://packages.medibuntu.org/ feisty free non-free
```
Then run 
```
sudo apt-get update
```

---

### Post by drs305 on 2008-05-29
> **rogerzoom said:**
> I am unable to open synaptic. Wont let me - a window pops up saying


When I open the medibuntu list I see this


Thanks for bearing with me ...
Okay, we are making progress. You have opened the medibuntu file. Highlight and delete everything in the file and replace it with this. Then save and close the file.
```

## Medibuntu - Ubuntu 8.04 LTS "hardy heron"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ hardy free non-free
deb-src http://packages.medibuntu.org/ hardy free non-free

```

---

### Post by FuturePilot on 2008-05-29
> **drs305 said:**
> Okay, we are making progress. You have opened the medibuntu file. Highlight and delete everything in the file and replace it with this. Then save and close the file.
```

## Medibuntu - Ubuntu 8.04 LTS "hardy heron"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
# deb http://packages.medibuntu.org/ hardy free non-free
# deb-src http://packages.medibuntu.org/ hardy free non-free

```

It looks like he's using Feisty though.

---

### Post by rogerzoom on 2008-05-29
Thanks - all sorted!

---

### Post by drs305 on 2008-05-29
> **FuturePilot said:**
> It looks like he's using Feisty though.

I think that is what the problem is, but perhaps we should ask:

rogerzoom, what version of ubuntu are you using?

ADDED:

If we had to do this again, I think we would keep it really simple and go about it like this:
```

sudo mv /etc/apt/sources.list.d/medibuntu.list /etc/apt/sources.list.d/medibuntu.list.bak
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update 

```

---

