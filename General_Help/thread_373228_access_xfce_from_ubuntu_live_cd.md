---
title: "access xfce from ubuntu live cd"
date: 2007-03-01
forum: General Help
---

### Post by shashi123 on 2007-03-01
I have a PC running on xubuntu but thre is a problem with the os its not booting now even in recovery mode

and i have a data to be taken from that pc

is there any way wherein i can access the harddisk from ubuntu live cd or xubuntu live cd or windows bootable 

plz help me with this 

thanx in advance

---

### Post by bodhi.zazen on 2007-03-01
> **shashi123 said:**
> I have a PC running on xubuntu but thre is a problem with the os its not booting now even in recovery mode

and i have a data to be taken from that pc

is there any way wherein i can access the harddisk from ubuntu live cd or xubuntu live cd or windows bootable 

plz help me with this 

thanx in advance

Sure ...

Boot to your live *buntu CD

list your partitions : ```
sudo fdisk -l
```

Mount your partition, I will assume /dev/hda1, but you will need to change ...

```
sudo mount /dev/hda1 /mnt
```

now you have root access.

ls /mnt should list your data.

Copy and back up what you will, CD/USB ...

HTH

---

### Post by shashi123 on 2007-03-01
thank you verymuch for ur valuable and immidiate responce bcoz of u i have been really able to save my valuable data 

just one more question 

in stability which one is better 

xubuntu 6.06 or 6.10 since i am using 6.10

thanx again

---

### Post by bodhi.zazen on 2007-03-01
> **shashi123 said:**
> thank you verymuch for ur valuable and immidiate responce bcoz of u i have been really able to save my valuable data 

just one more question 

in stability which one is better 

xubuntu 6.06 or 6.10 since i am using 6.10

thanx again

You are most welcome :p

IMO 6.06 is built for stability. 6.10 has now been out long enough that most of the "rough edges" have been worked out.

I would advise you take a look a 6.10 or even feisty for all but mission critical stuff.

---

### Post by shashi123 on 2007-03-01
one last query though my backup on desktop is done 

but my mozilla thunderbird mail folder when i try to access that folder fron nautilus it says permission denied and when i try to do from command line by using cp command it says its a read only folder so cannot copy 

how can i do this 

the folder is 

/mnt/home/Bhavana/Desktop/.mozilla-thunderbird/8ljk*^%.default/Mail

I want to copy this mail folder of thunderbird how can i access this when i see the property of Bhavana folder it says u r not the owner of this folder so cannot chagne permission of this folder 

plz let me know abt this 

thanx

---

### Post by bodhi.zazen on 2007-03-01
We mounted the partition as root.

What you can do is chmod ...

With the partition mounted at /mnt : ```
sudo chmod 777 /mnt
```

You should now have full access ;)

If that does not work, where are you truing to copy to ?

---

