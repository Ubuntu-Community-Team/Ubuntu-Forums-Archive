---
title: "Manually encryption and partitioning installing Ubuntu"
date: 2015-05-02
forum: General Help
---

### Post by squirrel2003 on 2015-05-02
I am trying to manually encrypt my ubuntu installation following a german description.
[http://wiki.ubuntuusers.de/System_verschl%C3%BCsseln](http://wiki.ubuntuusers.de/System_verschl%C3%BCsseln)

One of the last steps i am told to add the Module dm-crypt to /etc/modules

```
echo "dm-crypt" >> /etc/modules 
```

However (i started the Installation from a live DVD as told in the tutorial) the folder /etc/modules is not existing.
Can somebody help please, always when i try to save the state of the virtual machine during this installation process it is not restorable so i have to start from zero all over again.

---

### Post by squirrel2003 on 2015-05-02
I found it, it is a file not a folder, don't know why the searchfunction did not show it.

---

### Post by squirrel2003 on 2015-05-02
So in the next step i am encountering another problem. 
The tutorial tells me to edit /etc/initramfs-tools/modules.
 

 I shall execute  
 

 
```
echo "ohci_pci" >> /etc/initramfs-tools/modules  


```


 and as the next step  

 

 ```
update-initramfs -u -k all  


``` 

  However i am getting the message 
 update-initramfs is disabled since running on a read-only media

   
 I started from a live DVD as described in the tutorial.

---

### Post by squirrel2003 on 2015-05-06
It worked i failed with partitioning at first tries.

---

