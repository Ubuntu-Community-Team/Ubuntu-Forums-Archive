---
title: "Nautilus Displays Unmounted and Disconnected &quot;My Passport&quot; Folder Ubuntu 14.04.3"
date: 2016-02-05
forum: General Help
---

### Post by grace3 on 2016-02-05
Hello,

I have a 1TB WD Passport USB 2.0 HDD, that I very seldom use; however a folder labled "My Passport" sporadically pops-up for no apparent reason. I've checked /mnt & /dev and cannot find anything that could cause this. This behavior also persists after reboot.

Any help appreciated.

Grace

---

### Post by matt_symes on 2016-02-05
Hi

> **grace3 said:**
> Hello,

I have a 1TB WD Passport USB 2.0 HDD, that I very seldom use; however a folder labled "My Passport" sporadically pops-up for no apparent reason. I've checked /mnt & /dev and cannot find anything that could cause this. This behavior also persists after reboot.

Any help appreciated.

Grace

Where does it pop up ?

Are there any directories under /media ?

Kind regards

---

### Post by grace3 on 2016-02-06
> **matt_symes said:**
> Hi

Where does it pop up ?

Are there any directories under /media ?

Kind regards

It pops-up on the Desktop. BTW, as you suggested there was "/media/My Passport". I got rid of it with:

```
cd "/media/My Passport"
sudo rm -r "My Passport"
```

However, I suspect this is only a temporary fix. I expect that when I reconnect the device, I will have this problem again. I also wonder why it even pops-up on the Desktop to begin with.

Thanks, Grace

---

### Post by matt_symes on 2016-02-06
Hi

Just a word of warning.

You want to be careful running ```
sudo rm -r <directory>
```

If your external drive is mounted then it'll delete all the content on  that drive.

```
cd "/media/My Passport"
sudo rm -r "My Passport"
```

The above will remove the directory */media/My Passport*. However, it will also remove the contents of that directory and any sub directories.

You're better off running 

```
sudo rmdir "/media/My Passport"
```

The above command will not delete the directory is the directory is not empty or if the directory is currently the mountpoint for your external hard drive.

Kind regards

---

