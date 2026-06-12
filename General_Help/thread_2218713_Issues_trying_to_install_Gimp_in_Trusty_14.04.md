---
title: "Issues trying to install Gimp in Trusty 14.04"
date: 2014-04-21
forum: General Help
---

### Post by Cavsfan on 2014-04-21
I went to install Gimp in Trusty and am getting some weird errors. Synaptic does not show any broken packages. I wonder if anyone else has had this problem
```
cavsfan@cavsfan-desktop:~$ sudo apt-get install gimp
[sudo] password for cavsfan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gimp : Depends: libgegl-0.2-0 (>= 0.2.0) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

```
cavsfan@cavsfan-desktop:~$ sudo apt-get install libgegl-0.2-0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgegl-0.2-0 : Depends: libumfpack5.6.2 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

```
The following packages have unmet dependencies:
 libgegl-0.2-0 : Depends: libumfpack5.6.2 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
cavsfan@cavsfan-desktop:~$ sudo apt-get install libumfpack5.6.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libumfpack5.6.2 : Depends: libcholmod2.1.2 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

I'm not sure but, I think that goes on forever.

Synaptic appears kind of unstable in that when I select Gimp to install it sort of freezes and the dependencies take a while to get marked.
So I did not even try installing it there. Not sure which road to take.

I tried these to fix broken packages and still get the above error.

sudo apt-get autoremove
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get check
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update

---

### Post by 23dornot23d on 2014-04-21
[B]sudo apt-get install aptitude

sudo aptitude update

sudo aptitude install gimp


[/B]If unsure of options it should give back post what it says ..... answering no - sometimes gives more options
try not to remove anything important - if it should say it needs to remove something to complete its mission

Synaptic may be an option too - see if it reports any problems back when you go into it

**sudo synaptic**

( often use this when there is a report of broken packages - in the edit tab - 2nd from bottom - fix broken packages )

Possibly ...... the sources lists ....... are you using multiple PPAs .....

---

### Post by ibjsb4 on 2014-04-21
Looks like you tried everything except a dist-upgrade.

I tried installing 
```
ob1@ob1:~$ sudo apt-get install libumfpack5.6.2[sudo] password for ob1: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libamd2.3.1 libcamd2.3.1 libccolamd2.8.0 libcholmod2.1.2 libcolamd2.8.0
The following NEW packages will be installed:
  libamd2.3.1 libcamd2.3.1 libccolamd2.8.0 libcholmod2.1.2 libcolamd2.8.0
  libumfpack5.6.2
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 376 kB of archives.
After this operation, 1,852 kB of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.
ob1@ob1:~$ sudo apt-get install -s libumfpack5.6.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libamd2.3.1 libcamd2.3.1 libccolamd2.8.0 libcholmod2.1.2 libcolamd2.8.0
The following NEW packages will be installed:
  libamd2.3.1 libcamd2.3.1 libccolamd2.8.0 libcholmod2.1.2 libcolamd2.8.0
  libumfpack5.6.2
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Inst libamd2.3.1 (1:4.2.1-3ubuntu1 Ubuntu:14.04/trusty [i386])
Inst libcamd2.3.1 (1:4.2.1-3ubuntu1 Ubuntu:14.04/trusty [i386])
Inst libccolamd2.8.0 (1:4.2.1-3ubuntu1 Ubuntu:14.04/trusty [i386])
Inst libcolamd2.8.0 (1:4.2.1-3ubuntu1 Ubuntu:14.04/trusty [i386])
Inst libcholmod2.1.2 (1:4.2.1-3ubuntu1 Ubuntu:14.04/trusty [i386])
Inst libumfpack5.6.2 (1:4.2.1-3ubuntu1 Ubuntu:14.04/trusty [i386])
Conf libamd2.3.1 (1:4.2.1-3ubuntu1 Ubuntu:14.04/trusty [i386])
Conf libcamd2.3.1 (1:4.2.1-3ubuntu1 Ubuntu:14.04/trusty [i386])
Conf libccolamd2.8.0 (1:4.2.1-3ubuntu1 Ubuntu:14.04/trusty [i386])
Conf libcolamd2.8.0 (1:4.2.1-3ubuntu1 Ubuntu:14.04/trusty [i386])
Conf libcholmod2.1.2 (1:4.2.1-3ubuntu1 Ubuntu:14.04/trusty [i386])
Conf libumfpack5.6.2 (1:4.2.1-3ubuntu1 Ubuntu:14.04/trusty [i386])

```

---

### Post by Cavsfan on 2014-04-22
Synaptic shows no broken packages and I clicked Edit Fix Broken Dependencies but still get the same error.

None of these options look good:

```
cavsfan@cavsfan-desktop:~$ sudo aptitude install gimp
The following NEW packages will be installed:
  gimp gimp-data{a} libamd2.3.1{a} libbabl-0.1-0{a} libblas3{a} libcamd2.3.1{a} libccolamd2.8.0{a} libcholmod2.1.2{a} libgegl-0.2-0{a} libgfortran3{ab} libgimp2.0{a} libjavascriptcoregtk-1.0-0{a} 
  liblapack3{a} libmng2{a} libumfpack5.6.2{a} libwebkitgtk-1.0-0{a} libwebkitgtk-1.0-common{a} 
0 packages upgraded, 17 newly installed, 0 to remove and 0 not upgraded.
Need to get 18.7 MB of archives. After unpacking 87.1 MB will be used.
The following packages have unmet dependencies:
 libgfortran3 : Depends: gcc-4.8-base (= 4.8.2-17ubuntu2) but 4.8.2-19ubuntu1 is installed.
The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     gimp [Not Installed]                               
2)     libcholmod2.1.2 [Not Installed]                    
3)     libgegl-0.2-0 [Not Installed]                      
4)     libgfortran3 [Not Installed]                       
5)     liblapack3 [Not Installed]                         
6)     libumfpack5.6.2 [Not Installed]                    

     Leave the following dependencies unresolved:         
7)     gimp-data recommends gimp                          


Accept this solution? [Y/n/q/?] [COLOR=#ff0000]n[/COLOR]
The following actions will resolve these dependencies:

      Remove the following packages:                                      
1)      build-essential                                                   
2)      g++                                                               
3)      g++-4.8                                                           
4)      libstdc++-4.8-dev                                                 

      Downgrade the following packages:                                   
5)      cpp-4.8 [4.8.2-19ubuntu1 (now) -> 4.8.2-17ubuntu2 (trusty)]       
6)      gcc-4.8 [4.8.2-19ubuntu1 (now) -> 4.8.2-17ubuntu2 (trusty)]       
7)      gcc-4.8-base [4.8.2-19ubuntu1 (now) -> 4.8.2-17ubuntu2 (trusty)]  
8)      libasan0 [4.8.2-19ubuntu1 (now) -> 4.8.2-17ubuntu2 (trusty)]      
9)      libatomic1 [4.8.2-19ubuntu1 (now) -> 4.8.2-17ubuntu2 (trusty)]    
10)     libgcc-4.8-dev [4.8.2-19ubuntu1 (now) -> 4.8.2-17ubuntu2 (trusty)]
11)     libgomp1 [4.8.2-19ubuntu1 (now) -> 4.8.2-17ubuntu2 (trusty)]      
12)     libitm1 [4.8.2-19ubuntu1 (now) -> 4.8.2-17ubuntu2 (trusty)]       
13)     libquadmath0 [4.8.2-19ubuntu1 (now) -> 4.8.2-17ubuntu2 (trusty)]  
14)     libstdc++6 [4.8.2-19ubuntu1 (now) -> 4.8.2-17ubuntu2 (trusty)]    
15)     libtsan0 [4.8.2-19ubuntu1 (now) -> 4.8.2-17ubuntu2 (trusty)]      

      Leave the following dependencies unresolved:                        
16)     dpkg-dev recommends build-essential                               


Accept this solution? [Y/n/q/?] 

```

I entered "n" once and got the above. Answering "n" a few more times does not provide any suitable option that I want to take.
I've never seen this before. Gimp has always just installed even on the beta release. 
This is on the final release.

My software sources are as default except I checked Canonical Partners and left in Updates Pre-released Updates (trusty-proposed) unchecked.

---

### Post by Cavsfan on 2014-04-23
Has anyone successfully installed Gimp in Trusty without problems?

---

### Post by monkeybrain20122 on 2014-04-23
I just did after reading your thread, using good ole synaptic without a hitch. Trusty 64 bit.

Did you install something from a ppa and then disabled or removed the ppa? I don't mean the gimp ppa, but any ppa that might have upgraded some dependencies of those packages which cannot be installed now, my guess is that the installable versions are in a ppa that you have once used and then disabled/removed.

---

### Post by mc4man on 2014-04-23
gimp wants to install libgfortran3 except in your case it's the wrong version for gcc-4.8 that's  installed 
(gcc-4.8 is at 4.8.2-19ubuntu1, it wants to install libgfortran3 (4.8.2-17ubuntu2), you need libgfortran3  (4.8.2-19ubuntu1)

What does this show ?
```
apt-cache policy libgfortran3
```

are you using a mirror, if so switch to US server & update sources

---

### Post by SeijiSensei on 2014-04-23
> **Cavsfan said:**
> Has anyone successfully installed Gimp in Trusty without problems?

Sure.  I've been using GIMP since I installed the 14.04 Kubuntu alpha release some months back.  It survived every update along the way, too.

I used the PPA back with 12.04 when the standard version was 2.6.x, but the 14.04 repository version is 2.8.10, so now I use that.  I rarely add PPAs unless I know that there is something in the most recent version of a program that constitutes a substantial improvement in usability or security.

---

### Post by 23dornot23d on 2014-04-23
Strange that it should not go back in again but as monkeybrain20122 says

> 
I just did after reading your thread, using good ole synaptic without a hitch. Trusty 64 bit.


Mine is 64 bit too and Gimp went in on a fresh install but some weeks back now 

Maybe its just the 32 bit version would need for someone else to confirm this though.

Just checking my own** libgfortran3**

But if its all uptodate then cannot this be upgraded by itself .

> 
K53SV:~/Desktop$ apt-cache policy libgfortran3
libgfortran3:
  Installed: 4.8.2-19ubuntu1
  Candidate: 4.8.2-19ubuntu1
  Version table:
 *** 4.8.2-19ubuntu1 0
        500 [http://ubuntu.mirrors.uk2.net/ubuntu/](http://ubuntu.mirrors.uk2.net/ubuntu/) trusty/main amd64 Packages
        100 /var/lib/dpkg/status


---

### Post by mörgæs on 2014-04-23
I can't imagine that a 32 bit install shouldn't work when the 64 bit does, but anyway I tried and it all worked well.

23dornot, sorry to say but your posting style is putting strain on the reader. It takes time to read isolated statements. Real sentences have a better flow.

---

### Post by Cavsfan on 2014-04-24
> **mc4man said:**
> are you using a mirror, if so switch to US server & update sources

How is it you always just know the solution to my problems? :)

That was all it was! I usually do the test to see which servers are faster and select the one it finds for updates and in this case it was a mirror.
I had checked for updates prior to reading this and it just updated 3 files - the kernel.

Then I changed it back to the US server and it found 3 more updates. Gimp also installed without a problem.

Problem solved!

I had Gimp installed in prior to alpha install, alpha install, beta install. It was just the final released install that I had the problem with.

Guess I know better than to change the servers from now on! 
Thanks mc4man!

---

### Post by Cavsfan on 2014-04-24
> **monkeybrain20122 said:**
> I just did after reading your thread, using good ole synaptic without a hitch. Trusty 64 bit.

Did you install something from a ppa and then disabled or removed the ppa? I don't mean the gimp ppa, but any ppa that might have upgraded some dependencies of those packages which cannot be installed now, my guess is that the installable versions are in a ppa that you have once used and then disabled/removed.

You were on the right track with sources. But, mc4man nailed it with the mirror sources question. 
Few days go by that you do not learn something on this quest. :)

I'll leave the sources default from now on and we just seen a perfect example of why.

Thanks to all who posted!

---

