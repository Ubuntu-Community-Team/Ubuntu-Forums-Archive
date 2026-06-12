---
title: "Desperate - need CD for Hardy"
date: 2008-05-06
forum: General Help
---

### Post by John Jason Jordan on 2008-05-06
<Also posted to x86_64 forum; posted here in desperation for help>

I am writing this on my desktop because I have messed up the network on my laptop, which is my main computer. I messed it up by installing wicd in an attempt to fix the wireless after mupgrading from Gutsy to Hardy x86_64. However, I cannot reinstall network-manager because now I have no network at all on the laptop. The only way I will be able to reinstall network manager is via the CD. I have all the Hardy CDs, but nothing I can do will get Synaptic to see the CD.

In Synaptic I go to Settings > Repositories and then on the Third-Party Software tab. Then I click on the Add CD-ROM button, which pops up a box that says Please Insert a Disk into the Drive. I insert the Ubuntu Hardy desktop x86_64 CD in the drive and click on OK. A popup says "Scanning disc for index files, then "The disk is called <can't read the rest because it disappears too fast>." And then it says "unmounting CD-ROM." That's all it says, and afterwards Synaptic still does not see the CD-ROM. I am using Ubuntu Hardy x86_64 and I have tried other CDs as well, e.g., the Alternate Install CD. No way can I get Synaptic to see the CD drive.

If I can't get Synaptic to see the CD drive, how can I ever repair Network Manager?

I'm desperate here. I hope someone can help.

---

### Post by retrow on 2008-05-06
Go to your sources.list and comment out the line that looks for files from CD-ROM (i.e add # at the beginning) and save it.
```
sudo gedit /etc/apt/sources.list
```
In order to get the laptop onto network, you can connect it through ethernet (wired network). Usually you can easily connect via ethernet cable.
Then run,
```
sudo apt-get update
```.
Once you do this, you should be able to install whichever package you want with Synaptic.

---

### Post by John Jason Jordan on 2008-05-06
> **retrow said:**
> Go to your sources.list and comment out the line that looks for files from CD-ROM (i.e add # at the beginning) and save it.
```
sudo gedit /etc/apt/sources.list
```
In order to get the laptop onto network, you can connect it through ethernet (wired network). Usually you can easily connect via ethernet cable.
Then run,
```
sudo apt-get update
```.
Once you do this, you should be able to install whichever package you want with Synaptic.
Thanks, but without update manager I also have no ethernet. I currently have no network connection AT ALL. I must figure out how to repair from the CD. I do have all the Hardy CDs, but I can't get Synaptic to see them on the CD drive. Software Sources apparently has a bug and it cannot see the CD in the drive. Bad bug for a new release.

---

### Post by retrow on 2008-05-06
I think update manager is installed by default. Once you comment out the line that seeks files from CDROM, you should be able to run a ethernet based update through command line as I mentioned above.
```
sudo apt-get update
```
This does the same job as update manager.

---

### Post by John Jason Jordan on 2008-05-06
> **retrow said:**
> I think update manager is installed by default. Once you comment out the line that seeks files from CDROM, you should be able to run a ethernet based update through command line as I mentioned above.
```
sudo apt-get update
```
This does the same job as update manager.
No, that just gets me a lot of "failed to fetch" error messages.

I repeat: There is no network connection because the software required to connect to the ethernet has been removed. Wired and wireless are both dead.

I must figure out a way to reinstall the packages from the CD.

---

