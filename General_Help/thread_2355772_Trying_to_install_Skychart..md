---
title: "Trying to install Skychart."
date: 2017-03-16
forum: General Help
---

### Post by eddugo on 2017-03-16
Trying to install skychart with instruction from this site: [http://www.ap-i.net/skychart/en/documentation/installation_on_linux_ubuntu]("http://www.ap-i.net/skychart/en/documentation/installation_on_linux_ubuntu")

installed perfectly on my old machine, but got this message on my new one;


```
ed@Dell1:~$ sudo apt-get install --no-install-recommends skychart
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 skychart : Depends: libpng12-0 but it is not installable
E: Unable to correct problems, you have held broken packages.

```
Thank you in advance for advice

---

### Post by TheFu on 2017-03-16
You need to fix the "broken packages" issue first.

Start with:
```

sudo apt update
sudo apt upgrade
``` to see if there are any specific issues. Carefully read the output. Usually instructions to fix issues are provided. Follow those.

---

### Post by eddugo on 2017-03-16
Did these;
```
sudo apt update
sudo apt upgrade
```

And still got this;

```
All packages are up to date.
W: [http://www.ap-i.net/apt/dists/stable/InRelease:](http://www.ap-i.net/apt/dists/stable/InRelease:) Signature by key 5247B5CB921337EBBEFB0A5FC56CCB02D79BF92A uses weak digest algorithm (SHA1)
ed@Dell1:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.8.0-22 linux-headers-4.8.0-22-generic linux-headers-4.8.0-37
  linux-headers-4.8.0-37-generic linux-headers-4.8.0-38
  linux-headers-4.8.0-38-generic linux-image-4.8.0-22-generic
  linux-image-4.8.0-37-generic linux-image-4.8.0-38-generic
  linux-image-extra-4.8.0-22-generic linux-image-extra-4.8.0-37-generic
  linux-image-extra-4.8.0-38-generic linux-signed-image-4.8.0-37-generic
  linux-signed-image-4.8.0-38-generic ubuntu-core-launcher
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ed@Dell1:~$ sudo apt-get install --no-install-recommends skychart
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 skychart : Depends: libpng12-0 but it is not installable
E: Unable to correct problems, you have held broken packages.
ed@Dell1:~$
```

---

### Post by slickymaster on 2017-03-16
@eddugo:
Please [use code tags when posting output code]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168"). Output posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand. The use of code tags makes the post clean, compact and more appealing, thus getting more attention from readers.

---

### Post by TheFu on 2017-03-16
Did you try:

```
Use 'sudo apt autoremove' to remove them.
```
???
Also, if there are non-core PPAs, those could be causing issues. Remove them, run **apt update ** again and see if that helps.  Synaptic has a "fix broken packages" option or you can use **aptitude**. See if that helps.

---

### Post by eddugo on 2017-03-16
Tried all those things except aptitude - don't know what that is.  Synaptic says "successfully fixed dependency problems"  then I get the attached error message when trying to install skychart through synaptic: - update; just installed aptitude - didn't see a "broken package" option.

---

### Post by TheFu on 2017-03-16
Seems like you should seek help from the SkyChart people. It isn't a normal Ubuntu package. Their dependencies appear to be incorrect for your install.

---

### Post by eddugo on 2017-03-16
Ok, I will try that.  it did however, install on my 16.04 machine with no problems.

---

### Post by eddugo on 2017-03-16
TheFu;  

You are absolutely correct.   I went to a forum for Skymap and there are many folks with install problems in 16.10 - a file is missing in their software that was not needed in 16.04.  The unstable version has to be installed right now to get it working.  Here is a link to that forum in case you run across this again; [https://groups.yahoo.com/neo/groups/skychart-discussion/info]("https://groups.yahoo.com/neo/groups/skychart-discussion/info")

Thank you and sorry to have taken up your time on this.

I will mark it solved.

Ed

---

### Post by TheFu on 2017-03-16
Few people should actually run 16.10. Basically only developers, IMHO.  If you are an end-user, stay LTS.

---

