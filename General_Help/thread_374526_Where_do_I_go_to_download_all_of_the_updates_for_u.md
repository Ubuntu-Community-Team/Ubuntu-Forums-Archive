---
title: "Where do I go to download all of the updates for ubuntu manually."
date: 2007-03-02
forum: General Help
---

### Post by otazman on 2007-03-02
I would like to download all of the Ubuntu updates for 6.10 manually. How can I go about downloading them. i.e. where is the FTP sight that this information is pulled from? Once downloaded how can I point software updater to the downloaded file location?

Thanks, OT

---

### Post by usien on 2007-03-02
it is possible but i would highly recommend to leave it to synaptic to download and install the softwares automatically because sometimes version differences can cause instability.Anyways here is what you need to do:
1.Download the packages from packages.ubuntu.com
2.Save these to a folder
3.Run synaptic and from the menu File -> Add downloaded packages (you can also install the downloaded packages by just clicking on them but you will have to install all the dependencies by hand in that case)
4.Install the package

---

### Post by otazman on 2007-03-02
Wow, I didn't think there was so many packages. I have been learning how to use ubuntu and beryl in particular and have blown up my install more then once. Since it takes a while to download the updates so I can test I thought it would be easier to have all of the files on the network and pull them off instead of downloading again. 

Since there are so many packages is there a way to catch all of the files downloaded by the update manager and save them? I am assuming the update manager downloads the deb's, runs them and then deletes them. Anyway to get the update manager to either not delete the debs or to save them automatically?

OT

---

### Post by usien on 2007-03-02
all the .deb archives downloaded by apt/synaptic are saved in /var/cache/apt/archives

---

