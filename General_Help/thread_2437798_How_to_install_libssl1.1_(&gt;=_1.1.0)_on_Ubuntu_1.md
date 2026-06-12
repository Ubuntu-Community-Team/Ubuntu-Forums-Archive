---
title: "How to install libssl1.1 (&gt;= 1.1.0) on Ubuntu 16.04 ?"
date: 2020-02-29
forum: General Help
---

### Post by suaro on 2020-02-29
I'm trying to install shellinabox version 2.21 on Ubuntu 16.04

```
# cat /etc/*lsb*
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.6 LTS"
```

and I'm seeing the following error:

```
shellinabox depends on libssl1.1 (>= 1.1.0); however:
  Package libssl1.1 is not installed.

```
How can I install libssl1.1 (or greater) on Ubuntu 16.04 ?
I've done some searching but so far unable to find a way and hoping someone can provide some tips?
Unfortunately, I do not have an option to upgrade Ubuntu.  I'm stuck with 16.04 for now :( 

Thank you so much

---

### Post by DuckHook on 2020-02-29
You are playing with fire here. Xenial still uses version 1.0 of this library, and since SSL is such an integral part of the OS, forcing it to use v.1.1 would likely break your install at a very fundamental level. If I were you, I would just install the Xenial version of shellinabox or spin up a Bionic VM to run the version you want.

It is not a good idea to monkey around with backports on critical system files. IMO, it is not a good idea for general users to monkey around with backports, ever, but that's my personal opinion.

---

### Post by suaro on 2020-02-29
I do have Xenial version of shellinabox installed and it works fine; however; I have to remove it due to DOS vulnerability or upgrade to 2.2.1  and alas that's where I'm at :(
Thanks so much for your feedback.   It sounds like libssl1.1 isn't support with Xenial and trying to shoe horn it - may not be a good idea.  I'll remove shellinabox for now.  Thanks again.

---

### Post by DuckHook on 2020-02-29
If you can download Eoan, you might consider the VM route. Install Eoan on a VM (Ubuntu already comes with KVM in the kernel), then install shellinabox in the Eoan VM, and it would all be up to date. VMs are wonderfully flexible and robust, but the process does have a learning curve and may be more trouble than it's worth to you. We don't know how mission-critical shellinabox is to you. Forum Members may be able to better advise you about alternatives if you tell us what you use shellinabox for.

---

### Post by suaro on 2020-02-29
If I understand correctly, are you suggesting to install updated version of shellinabox into a VM or docker instance ?  (i.e. [https://github.com/sspreitzer/docker-shellinabox#introduction](https://github.com/sspreitzer/docker-shellinabox#introduction) ) .
I could definitely go this route but not sure how containerized or VM flavor of shellinabox would provide login access to the host machine?  Seems like it could be useful to provide a login instance to a user inside a container which could be helpful in other scenarios.  In my case, sshd may be stopped on the host machine and having shellinabox is a life saver. Just wish I could get the latest version working with [COLOR=#000000]Xenial  .  Thanks for all the feedback.  Its very helpful!![/COLOR]

---

### Post by mc4man on 2020-02-29
If your issue is shellinabox version & not libssl version then maybe try building latest git of shell... (it's about 1 yr. old anyway.
Shouldn't take more than a couple of minutes, the git source will build a .deb package for you..
[Instructions here]("https://github.com/shellinabox/shellinabox"), just install the dependencies and then skip down to the [debian section ]("https://github.com/shellinabox/shellinabox#debian-package")

edit:
I'd change the suggested package build command to this, prevents a warning..
```
dpkg-buildpackage -b -us -uc
```

---

### Post by suaro on 2020-02-29
Using this docker image: -> [https://github.com/spali/docker-shellinabox](https://github.com/spali/docker-shellinabox)     works perfectly.  I start the image using:

 docker run -d --name shellinabox -p 4200:4200-e SHELLINABOX_SERVICE_HOST=host -e SHELLINABOX_SERVICE_WHO=who -eSHELLINABOX_SERVICE_LOCAL=local -e SHELLINABOX_ALLOW_SUDO=1 -eSHELLINABOX_USER=myuser -e SHELLINABOX_PASSWORD=mypassword -eSHELLINABOX_DISABLE_SSL=1 -e SHELLINABOX_DEFAULT=host spali/shellinabox

..and able to log into the host machine without any problems.  Unfortunately, this image hasn't been updated in 5 years so I suspect its running an older version of shellinabox. 

This one ->  [https://github.com/sspreitzer/docker-shellinabox#introduction ]("https://github.com/sspreitzer/docker-shellinabox#introduction") would be ideal ; however;  i can only access a shell within the container (not the host machine ) .
The configuration options don't seem to map to the ones available on the first link although a reference to the top link is provided .

I do think this might be the way to go and I'll need to study the second one ([https://github.com/sspreitzer/docker-shellinabox#introduction](https://github.com/sspreitzer/docker-shellinabox#introduction) ) with the later image to see what options I can pass. 
Thanks for the tip.  I've got some studying to do ...  If you or anybody just happens to know that would be a wonderful welcome.

---

### Post by suaro on 2020-02-29
@[mc4man]("https://ubuntuforums.org/member.php?u=320715")[COLOR=#000000]    What version of ubuntu are you using from your desktop ?  I can give this a try and post back.  Earlier I tried to build , but when attempting to install is when I ran into the libssl1.1 issue.  I'm stuck on 16.04 (xenial ) [/COLOR]

---

### Post by suaro on 2020-02-29
[COLOR=#000000]@[/COLOR][mc4man]("https://ubuntuforums.org/member.php?u=320715")  Thanks,  i built the package using the steps provided and it worked like a charm.  Problem solved.  Thanks  mc4man and duckhook

---

### Post by suaro on 2020-02-29
[COLOR=#000000][COLOR=#000000]@[/COLOR][/COLOR][mc4man]("https://ubuntuforums.org/member.php?u=320715")[COLOR=#000000]  Would you happen to know offhand how I can build v2.21 ?   Latest tag ( [/COLOR][https://github.com/shellinabox/shellinabox](https://github.com/shellinabox/shellinabox) ) shows v.2.20[COLOR=#000000] and the DOS vulnerability fix is in 2.21
Its strange because I do see references to v.2.21  ( [/COLOR][https://github.com/shellinabox/shellinabox/commit/4f0ecc31ac6f985e0dd3f5a52cbfc0e9251f6361](https://github.com/shellinabox/shellinabox/commit/4f0ecc31ac6f985e0dd3f5a52cbfc0e9251f6361) ) and the updated source to correct the vulnerability, but I don't see a tag that I can git clone. (maybe just my ignorance about how git works :( )

---

### Post by mc4man on 2020-03-01
> **suaro said:**
> [COLOR=#000000][COLOR=#000000]@[/COLOR][/COLOR][mc4man]("https://ubuntuforums.org/member.php?u=320715")[COLOR=#000000]  Would you happen to know offhand how I can build v2.21 ?   Latest tag ( [/COLOR][https://github.com/shellinabox/shellinabox](https://github.com/shellinabox/shellinabox) ) shows v.2.20[COLOR=#000000] and the DOS vulnerability fix is in 2.21
Its strange because I do see references to v.2.21  ( [/COLOR][https://github.com/shellinabox/shellinabox/commit/4f0ecc31ac6f985e0dd3f5a52cbfc0e9251f6361](https://github.com/shellinabox/shellinabox/commit/4f0ecc31ac6f985e0dd3f5a52cbfc0e9251f6361) ) and the updated source to correct the vulnerability, but I don't see a tag that I can git clone. (maybe just my ignorance about how git works :( )

Edit, misread post... will take a look..

---

### Post by mc4man on 2020-03-01
For 2.21 (whether much different no clue..) you'd go here
[https://launchpad.net/ubuntu/+source/shellinabox/2.21](https://launchpad.net/ubuntu/+source/shellinabox/2.21)
Download both the the .tar.xz & .dsc files, create a new folder & place both inside.
Then open a terminal at the new folder & go
```
dpkg-source -x ./shellinabox_2.21.dsc && cd shellinabox-2.21
```

```
sudo apt install debhelper binutils 
```
(- must be at least debhelper 9, should be..

Then same as before
```
dpkg-buildpackage -b -us -uc
```

---

### Post by mörgæs on 2020-03-01
> **suaro said:**
> 
Unfortunately, I do not have an option to upgrade Ubuntu.  I'm stuck with 16.04 for now

Maybe this is your real problem. If this gets solved then everything related to libssl falls into place.

---

### Post by suaro on 2020-03-01
> **mc4man said:**
> For 2.21 (whether much different no clue..) you'd go here
[https://launchpad.net/ubuntu/+source/shellinabox/2.21](https://launchpad.net/ubuntu/+source/shellinabox/2.21)
Download both the the .tar.xz & .dsc files, create a new folder & place both inside.
Then open a terminal at the new folder & go
```
dpkg-source -x ./shellinabox_2.21.dsc && cd shellinabox-2.21
```

```
sudo apt install debhelper binutils 
```
(- must be at least debhelper 9, should be..

Then same as before
```
dpkg-buildpackage -b -us -uc
```

Thanks for these details.  I was able to successfully build a package -> shellinabox_2.21_amd64.deb and install on my servers.
I also verified the DOS exploit is fixed by running the follow test against the new install vs. the older one:

```
curl -v --header "Content-type: multipart/form-data;boundary=------------------------8d14c0216fd84557" -d "impeachment" http://10.0.0.5:4200/s/
```

The call issued to older node sends shellinabox to 100% CPU.  Same call against newer build from above has no affect on shellinabox so it appears to have the DOS exploit fixed.

Something odd though (and maybe just a version bug within shellinabox ) , but on a fresh box with no prior installs of shellinabox and using the newly created package ( shellinabox_2.2**1**_amd64.deb ) ,  the version shows 2.20 after an install. 

# /usr/bin/shellinaboxd --version
ShellInABox version 2.20

Must be a version bug since this is really 2.21 (as verified using the exploit test above.)
Anyhoo, thanks everyone .  This has been a great learning experience for me!

---

### Post by mc4man on 2020-03-01
As I don't use wasn't quite paying attention.
Both the git and launchpad sources and resultant packages should be exactly the same, to see just look inside the sources > Debian/changelog

No one bothered to change the source define of version  from 2.20 to 2.21, ( likely in configure.ac), the only change  was to the package name itself..

---

