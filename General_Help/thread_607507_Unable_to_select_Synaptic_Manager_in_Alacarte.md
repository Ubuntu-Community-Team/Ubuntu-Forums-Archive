---
title: "Unable to select Synaptic Manager in Alacarte"
date: 2007-11-09
forum: General Help
---

### Post by speedforu on 2007-11-09
Hi All,
I have recently installed Ubuntu 7.10 on my Dell Vostro 1500 and I should say that it was a beauty.
Everything seemed to work fine untill one day when I noticed that there is no Synaptic Manager menu item in the menu. I have read some posts regarding the usage of Alacarte to select the items to be appearing in the menu bar. So, I open alacarte from the terminal and it opens up a GUI to check/uncheck applications, but sadly when I check the 'Synaptic Manager' it automatically gets unchecked no matter how many times I tried. Infact it is the same case with all the menu items appearing under System->Administration section. I guess there is something fishy about the administrative privileges but I am not able to figure out that. 

one more thing, I have a dual boot setup with Windows XP and when I run Ubuntu sometimes I was able to access the NTFS partitions (able to read/write and modify) but recently I notice that I no longer can view those partitions from Ubuntu. SOMETHING FISHY GOING AROUND ;-)

Guys, please help me and make my experience with Ubuntu wonderful.

---

### Post by zvacet on 2007-11-09
Do you see synaptic in **system<administration<synaptic package manager**?You can not add any administrative program unless you have admin privileges.Chek in **users&groups** do you have admin privileges.Do you have two accounts?

---

### Post by por100pre1 on 2007-11-09
Check if the command is correct. It should be like this:

```
gksu /usr/sbin/synaptic
```

---

### Post by speedforu on 2007-11-10
i have tried "gksu /usr/sbin/synaptic" from the command  prompt and I can see the synaptic manager and can install programs using that gui, but I am not able to select the synaptic manager tool item in the alacarte somehow. I am the only user of the computer and I also do not see the Users Groups option in the tool bar.

---

### Post by ridgeland on 2007-11-14
speedforu,
I had the problem of auto-unclick.
I got mine working.  see my post in
[http://ubuntuforums.org/showthread.php?t=604877](http://ubuntuforums.org/showthread.php?t=604877)
Remember to make a backup before editing any system file.

---

### Post by speedforu on 2007-11-16
> **ridgeland said:**
> speedforu,
I had the problem of auto-unclick.
I got mine working.  see my post in
[http://ubuntuforums.org/showthread.php?t=604877](http://ubuntuforums.org/showthread.php?t=604877)
Remember to make a backup before editing any system file.

Hi,
I tried doing wat u have said, the problem is that i can get the System tools without any problem without doing wat u have described in ur post but I am not able to find any option related to the 'Administration ' sub menu. I searched in the other menus and all i see is " <!-- System Settings -->
  <Menu>
    <Name>Administration</Name>
    <Directory>System-Settings.directory</Directory>
    <Include>
      <And>
        <Category>Settings</Category>
        <Category>System</Category>
      </And>
    </Include>
  </Menu>     <!-- End System Settings -->

  <Layout>
    <Menuname>Preferences</Menuname>
    <Menuname>Administration</Menuname>
  </Layout>

</Menu> <!-- End Settings -->
"
and I could find nothing in the System-Settings.directory;

I think there is some thing hapnd becoz after which I see such anamolies in the system like the disappearance of the menu items, disapperance of the NTFS and FAT32 drives, disapperance of the Add Remove Applications.

Its time that the Linux gurus should come to the rescue. (I dont want to reinstall the OS :lolflag:)

---

### Post by ridgeland on 2007-11-17
Please use English words.
u no only 1 hu rd it.

I just checked in alacarte and I can edit the menu for System -> Adminstration.  Once I got the other options to accept changes I see I can also make changes in Adminstration.

It may be time to reinstall if lots of other things are broken too.

---

