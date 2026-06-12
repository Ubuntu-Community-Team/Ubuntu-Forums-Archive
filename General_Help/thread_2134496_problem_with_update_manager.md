---
title: "problem with update manager"
date: 2013-04-11
forum: General Help
---

### Post by babakflame on 2013-04-11
Dear Buddies
Hi
Whenever I try to eceute update manager, I confront this error:
[HTML]Requires installation of untrusted packages

The action would require the installation of packages from not authenticated sources.
deluge deluge-common deluge-gtk libgdata-common libgdata13 ttf-mscorefonts-installer
[/HTML]

What should I do buddies?

---

### Post by ibjsb4 on 2013-04-11
Looks to be missing a key :)

Open a terminal and enter:

```
sudo apt-get update
```

And please post using code tags

[ATTACH=CONFIG]241222[/ATTACH]

---

### Post by gordintoronto on 2013-04-11
What repositories have you added to your Software Sources? What version of Ubuntu?

If you have not added repositories, those packages should be OK.

---

### Post by babakflame on 2013-04-12
Dear Buddies
Hi

I ran sudo apt-get update in terminal and in the last lines I got these error:
My ubuntu is 11.10


```
Fetched 5,414 B in 27s (196 B/s)                         
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://ir.archive.ubuntu.com oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://ir.archive.ubuntu.com oneiric-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://ppa.launchpad.net oneiric Release: The following signatures were invalid: BADSIG C5E6A5ED249AD24C Launchpad PPA for Deluge Team
W: GPG error: http://ppa.launchpad.net oneiric Release: The following signatures were invalid: BADSIG 3BDAAC08614C4B38 Launchpad otto06217
W: GPG error: http://ppa.launchpad.net oneiric Release: The following signatures were invalid: BADSIG 86D36DFDE6A250EA Launchpad PPA for skypewrapper
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/oneiric/Release  

W: Failed to fetch gzip:/var/lib/apt/lists/partial/ir.archive.ubuntu.com_ubuntu_dists_oneiric_main_binary-amd64_Packages  Encountered a section with no Package: header

W: Failed to fetch gzip:/var/lib/apt/lists/partial/ir.archive.ubuntu.com_ubuntu_dists_oneiric_universe_binary-amd64_Packages  Encountered a section with no Package: header

W: Failed to fetch gzip:/var/lib/apt/lists/partial/ir.archive.ubuntu.com_ubuntu_dists_oneiric_multiverse_binary-amd64_Packages  Encountered a section with no Package: header

W: Some index files failed to download. They have been ignored, or old ones used instead.
```
babak@babak-VPCEA26FG:~$

Regards
  Bobi

---

### Post by ibjsb4 on 2013-04-12
GPG error BADSIG
[http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html](http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html)

more here
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=GPG+error+BADSIG&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=GPG+error+BADSIG&sa=Search&cof=FORID:9)

---

### Post by babakflame on 2013-04-13
Hi ibjsb4

I used one of the methods in the sites you mentioned:

```
[INDENT]sudo aptitude -o Acquire::http::No-Cache=True -o Acquire::BrokenProxy=true update

 sudo apt-get update

[/INDENT]
```

however I confont this error:
```
sudo: aptitude: command not found
```
then I ran 
```

sudo apt-get install multiget
```
However, after that I have this on my terminal without any changing:
Package configuration                                                           
                                                                                
 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring ttf-mscorefonts-installer &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474;                                                                           &#9474;  
 &#9474; single entity) and Microsoft Corporation for the Microsoft software          
 &#9474; accompanying this EULA, which includes computer software and may include     
 &#9474; associated media, printed materials, and "on-line" or electronic             
 &#9474; documentation ("SOFTWARE PRODUCT" or "SOFTWARE"). By exercising your         
 &#9474; rights to make and use copies of the SOFTWARE PRODUCT, you agree to be       
 &#9474; bound by the terms of this EULA. If you do not agree to the terms of         
 &#9474; this EULA, you may not use the SOFTWARE PRODUCT.                             
 &#9474;                                                                              
 &#9474; SOFTWARE PRODUCT LICENSE The SOFTWARE PRODUCT is protected by copyright      
 &#9474; laws and international copyright treaties, as well as other intellectual     
 &#9474; property laws and treaties. The SOFTWARE PRODUCT is licensed, not sold.      
 &#9474;                                                                              
 &#9474; 1. GRANT OF LICENSE. This EULA grants you the following rights:              
 &#9474;                                                                              
 &#9474;                                                                              
 &#9474;                                  <Ok>                                        
 &#9474;                                                                           &#9474;  
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;  
                                                                                
                    what should I do now?

Regards
 Bobi

---

### Post by babakflame on 2013-04-13
Hi 
After about 3o minutes, I log out the system, then I tried the 
```

sudo apt-get install multiget
```
again, Howver now this appears on terminal:babak@babak-VPCEA26FG:~$ ```
sudo apt-get install multiget
[sudo] password for babak: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


```

would somebody plz help me for god's sake, what should I do?:confused::(:confused::(

---

### Post by ibjsb4 on 2013-04-13
> Configuring ttf-mscorefonts-installer

GRANT OF LICENSE. This EULA grants you the following rights:
<Ok>

Use the "Tab" key and "Enter"

---

### Post by babakflame on 2013-04-14
Hi   ibjsb4

    When I ran ```
sudo apt-get install multiget
```
this appears in the last lines in terminal:

```
babak@babak-VPCEA26FG:~$ sudo apt-get install multiget
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libntfs10
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  multiget
0 upgraded, 1 newly installed, 0 to remove and 59 not upgraded.
1 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/cache/apt/archives/
babak@babak-VPCEA26FG:~$ 

```

Would you plz help me what is the problem now?:mad::mad::confused::confused:

  Regards
   Bobi

---

### Post by prc292 on 2013-04-14
I've got the same problem with update manager right now and can't solve it either although I'm connected to public WiFi and suspect that somehow I'm being blocked from the update server and can't get these keys. I'm relatively new to Linux but usually when I get this "unable to get a lock.." Message its because some other recourse is already using it. Either something else is trying to update or software manger is doing something or another program is trying to update at the same time. Either find the conflicting programs or just reboot and try again.

---

### Post by babakflame on 2013-04-14
Dear Buddies
Hi
Eventually I succeed to ran these directives :

```

sudo aptitude -o Acquire::http::No-Cache=True -o Acquire::BrokenProxy=true update   sudo apt-get update
```

However, The error: [PHP] Requires installation of untrusted packages[/PHP]

is still appearing, I think its because of Deluge Bittorrent client application
Because this is seen in details of error:

[PHP]deluge deluge-common deluge-gtk libgdata-common libgdata13[/PHP]

What can I do for this application for solving this problem with update manager?:confused::confused:

---

### Post by Vaphell on 2013-04-14
do you get deluge from PPA? Looks like you have it unsigned
[https://launchpad.net/+help-soyuz/ppa-sources-list.html](https://launchpad.net/+help-soyuz/ppa-sources-list.html)

---

### Post by babakflame on 2013-04-14
Hi vaphell
What you have posted seems interesting:), Nevertheless I am still novice with ubuntu and I got problem with this line::confused:
[PHP]On the PPA's overview page, look for the       heading that reads Adding this PPA to your system. Make a note       of the PPA's location, which looks like:                  ppa:gwibber-daily/ppa     

[/PHP] 

Where is PPA overview page and how can I find it?

Regards
  Bobi

---

### Post by Vaphell on 2013-04-14
that info page meant the main page of the ppa one is interested in.
in case of deluge it would be this: [https://launchpad.net/~deluge-team/+archive/ppa](https://launchpad.net/~deluge-team/+archive/ppa) (repository maintained by deluge team in case you are not happy with the version found in official repositories). It shows this string: **ppa:deluge-team/ppa**

But did you add deluge repository to the list of repositories your system pulls packages from? Check in 'Software sources' (Software Center->Edit->Software Sources->Other Sources)

---

### Post by babakflame on 2013-04-17
Hi vaphell
First, I checked the route you had mentioned:  Software Center->Edit->Software Sources->Other Sources

The checkmark of [http://ppa.launchpad.net/deluge-team](http://ppa.launchpad.net/deluge-team)  was ON.

Then I did exactly as it said in  
[HTML]How do I use software from a PPA?
[/HTML]

however I still have this in terminal:
```
Fetched 2,265 kB in 4min 30s (8,362 B/s)
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net oneiric Release: The following signatures were invalid: BADSIG C5E6A5ED249AD24C Launchpad PPA for Deluge Team
W: GPG error: http://ir.archive.ubuntu.com oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://ir.archive.ubuntu.com oneiric-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://ppa.launchpad.net oneiric Release: The following signatures were invalid: BADSIG 3BDAAC08614C4B38 Launchpad otto06217
W: GPG error: http://ppa.launchpad.net oneiric Release: The following signatures were invalid: BADSIG 86D36DFDE6A250EA Launchpad PPA for skypewrapper
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/oneiric/Release  

W: Some index files failed to download. They have been ignored, or old ones used instead.
```

As it can be seen the ubuntu did not Fetch the deluge PPA key. So there is still my problem in update manager with Other Updates:(:(:confused:

---

### Post by dino99 on 2013-04-17
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by Vaphell on 2013-04-17
does it update when you disable everything but the standard repo?

maybe something like this
[http://www.maketecheasier.com/solve-badsig-error-in-ubuntu/2012/01/13](http://www.maketecheasier.com/solve-badsig-error-in-ubuntu/2012/01/13)

---

### Post by babakflame on 2013-04-18
Hi buddies
I think that eventually my problem solved :guitar::):guitar: and I ran the 
```
sudo apt-get upade
```  without any BADSIG error.

  Best Regards

  Bobi

---

