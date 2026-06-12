---
title: "libc6 has unmet dependencies, unable to correct dependencies"
date: 2015-07-28
forum: General Help
---

### Post by stereostan on 2015-07-28
Hi, my package manager is broken, I can't update anything. It all comes back to:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
 libc6 : Depends: libc-bin (= 2.15-0ubuntu10.12) but 2.15-0ubun|u10.12 is installed

And I'm at the limit of my knowledge. Is this just a corrupted filename? I've sudo apt-get install -f to no avail. Help?

---

### Post by dino99 on 2015-07-29
i suppose you met that issue due to 'third party' app/package installation conflicting with the genuine version: stay on the ubuntu archive and you then will avoid such trouble. Either uninstall these non trusted app/package or downgrade to the genuine version (using synaptic is a friendly way to deal with such problem)

---

### Post by stereostan on 2015-07-29
dino99 thanks. I'm too much of a noob to have knowingly installed anything that wasn't from the ubuntu repositories, or so I thought. I've only installed a few apps that didn't come with the ubuntu 12.0?LTS installer, and the other apps I did install came only from the ubuntu software center. I'm wrong in assuming that software from the software center is OK?

---

### Post by steeldriver on 2015-07-29
Does it really say

```

2.15-0ubun[COLOR=#ff0000]**|**[/COLOR]u10.12 is installed

```

If so, I'd suspect a corrupted package file - maybe /var/lib/dpkg/status?

---

### Post by stereostan on 2015-07-30
Yes, steeldriver, that's what it says and what the corrupted file was my thought. Forgive my ignorance, what does "/var/lib/dpkg/status" do? I'm getting a "no such command found" in terminal. And an additional problem, I can't install or remove software in the software center until my unresolved dependencies are met, which I can't do.

---

### Post by tgalati4 on 2015-07-31
Welcome to the forums.

Try:

```
sudo apt-get clean
sudo apt-get check
```

And finally:

```
apt-cache policy libc6
```

It might look something like:

> tgalati4@Mint17 ~ $ apt-cache policy libc6
libc6:
  Installed: 2.19-0ubuntu6.6
  Candidate: 2.19-0ubuntu6.6
  Version table:
 *** 2.19-0ubuntu6.6 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main amd64 Packages
        100 /var/lib/dpkg/status
     2.19-0ubuntu6 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages


---

### Post by stereostan on 2015-08-04
thanks for the reply, tgalati4, I tried your suggestions, it's still hosed. BTW this is a 12.04 LTS install on a Compaq laptop. Output from terminal:
stan@StansLaptop:~$ sudo apt-get clean
[sudo] password for stan: 
stan@StansLaptop:~$ sudo apt-get clean
stan@StansLaptop:~$ sudo apt-get check
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libc6 : Depends: libc-bin (= 2.15-0ubuntu10.12) but 2.15-0ubun|u10.12 is installed
E: Unmet dependencies. Try using -f.
stan@StansLaptop:~$ apt-cache policy libc6
libc6:
  Installed: 2.15-0ubuntu10.12
  Candidate: 2.15-0ubuntu10.12
  Version table:
 *** 2.15-0ubuntu10.12 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main i386 Packages
        100 /var/lib/dpkg/status
     2.15-0ubuntu10.11 0
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main i386 Packages
     2.15-0ubuntu10 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main i386 Packages

---

### Post by stereostan on 2015-08-04
Is it possible to rename 2.15-0ubun|u10.12? Just a noob thought.

---

### Post by dino99 on 2015-08-04
Forget about the Software Center; its to dangerous (third untrusted sources available) and too buggy; use synaptic instead, it will show you which package(s) have unmet dependency (ies) and will allow you to purge the faulty one(s)

> sudo apt-get install synaptic
sudo synaptic

---

### Post by stereostan on 2015-08-04
dino99, thanks for the reply. I'm still hosed. Terminal output:

stan@StansLaptop:~$ sudo apt-get install synaptic
[sudo] password for stan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libc6 : Depends: libc-bin (= 2.15-0ubuntu10.12) but 2.15-0ubun|u10.12 is to be installed
 synaptic : Depends: libept1.4.12 but it is not going to be installed
            Depends: libvte9 (>= 1:0.24.0) but it is not going to be installed
            Recommends: rarian-compat but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
stan@StansLaptop:~$ sudo synaptic
sudo: synaptic: command not found
stan@StansLaptop:~$

---

### Post by steeldriver on 2015-08-04
Let's see if we can figure out where the mysterious 2.15-0ubun|u10.12 is coming from - can you post the output of

```

diff /var/lib/dpkg/status{,-old}

```

please?

---

### Post by stereostan on 2015-08-04
thanks  for the reply steeldrive.Terminal output:

stan@StansLaptop:~$ diff /var/lib/dpkg/status{,-old}
30844c30844
< Status: deinstall ok installed
---
> Status: install ok installed
stan@StansLaptop:~$

---

### Post by mc4man on 2015-08-04
You could consider downloading the proper package & seeing if dpkg would install it if you can't find the error 'entry'
something like this - 
```
mkdir -p fix1 && cd fix1
```
```
wget http://launchpadlibrarian.net/201322489/libc-bin_2.15-0ubuntu10.12_i386.deb
```
```
sudo dpkg -i ./libc-bin_2.15-0ubuntu10.12_i386.deb
```
or maybe  it would fail  due to different package name ?? so this instead - 
```
sudo dpkg --force-overwrite -i ./libc-bin_2.15-0ubuntu10.12_i386.deb
```

---

### Post by stereostan on 2015-08-09
I think maybe step 2 and step 4 did the trick. It is installing updates now and that's better than it has been working thanks mc4man

---

