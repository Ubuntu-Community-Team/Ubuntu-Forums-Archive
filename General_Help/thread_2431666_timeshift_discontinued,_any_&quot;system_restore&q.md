---
title: "timeshift discontinued, any &quot;system restore&quot; style alternatives?"
date: 2019-11-20
forum: General Help
---

### Post by nocruoro on 2019-11-20
Trying to makw my computer go back to a earlier time to fix a broken uninstallation but it looks like TimeShift is nowhere to be found. Does anyone know any easy programs similar to "Windows System Restore "that can check the system for restore point earlier ?

---

### Post by guiverc on 2019-11-20
You haven't said what release of Ubuntu you are using, but `timeshift` is available for recent releases - [https://packages.ubuntu.com/search?suite=all&searchon=names&keywords=timeshift](https://packages.ubuntu.com/search?suite=all&searchon=names&keywords=timeshift)

---

### Post by Artim on 2019-11-20
I really like Systemback.  Find it [here](https://www.linuxbabe.com/ubuntu/install-systemback-ubuntu-18-04-bionic-18-10).

---

### Post by speartip on 2019-11-20
Timeshift hasn't been discontinued as far as I know. If you're running the latest LTS though, it's not in the repos. You will have to add the ppa 1st, as per instructions here:
[https://teejeetech.in/2019/08/11/timeshift-v19-08/](https://teejeetech.in/2019/08/11/timeshift-v19-08/)

---

### Post by nocruoro on 2019-11-20
Im using Ubuntu 18.04.3 LTS Bionic Beaver, I forget to say it so often. 


But managed to install it with

> sudo add-apt-repository -y ppa:teejee2008/timeshift
sudo apt update
sudo apt install timeshift


But i cant get it to find a snaphot before timeshift installation. This is intended as a  last resort to fix a unmet dendencies and broken packages and standard solutions havent worked. Bad attempt to move a file in Leocad led to removal and the installation wont re-install.
Do i need a different program fix this or can a repair install of Ubuntu beaver fix this?. No sudo commands have worked for force installing.

---

### Post by GhX6GZMB on 2019-11-20
I suspect you've had an HDD crash or have replaced your HDD.
To get a Timeshift snapshot to load, you'll need to change the UUID of your present HDD to the UUID of the disk the Timeshift snapshot you're trying to restore.

---

### Post by nocruoro on 2019-11-21
> **ml9104 said:**
> I suspect you've had an HDD crash or have replaced your HDD.
To get a Timeshift snapshot to load, you'll need to change the UUID of your present HDD to the UUID of the disk the Timeshift snapshot you're trying to restore.

The hard drive was fine but windows 10 boot manager was damaged so my best option was to install a safer operating system like ubuntu with a usb. been using it for 2 months.

---

### Post by mastablasta on 2019-11-21
there is also a built in option in the form of file systems like BTRFS and TFS4linux. both support snapshots of the drive.

---

### Post by nocruoro on 2019-11-21
Might have to consider dropping Installing Leocad and re-install ubuntu if i get issues with other installing programs

---

### Post by treesloth on 2019-11-22
I was also looking for a good backup system recently.  I'm currently using Cronopete and am happy with it so far.  It's been in use for about 2 months.  I don't know much about its restore capabilities, though, as I've only had to do that once.  But, so far so good.

---

