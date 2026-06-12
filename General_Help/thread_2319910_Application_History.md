---
title: "Application History"
date: 2016-04-08
forum: General Help
---

### Post by Lightning Dragon on 2016-04-08
Hello,

I'm trying to help my friend with his install of Ubuntu on a spare laptop. Everything installed well etc etc, except we noticed that none of this applications seem to remember its history even when that application has been set to remember from within itself. For example, Libreoffice will forget documents, Spotify will forget source lists (forcing him to re-add folders), terminal will not remember commands, Okular will forget recent documents etc etc. He has to re-add everything *every* time he reboots the laptop, which he doesn't like to do. I thought maybe the issue I had from [this thread could be it]("http://ubuntuforums.org/showthread.php?t=2273574"), but he followed the same steps and it didn't seem to solve anything. We dug through his settings just in case something was changed but everything seems just fine, so now I have no idea what else to suggest him to try.

Any help? He's looking to use this for college work and Ubuntu losing its information every reboot is going to make it difficult. 

Thanks!

---

### Post by grahammechanical on 2016-04-08
Did you create a partition for data? Or stick to the traditional layout of everything in a home folder in / or even a /home partition?

If our documents are stored in another partition that is not being mounted at boot time, then applications will not be able to find the recently used files. The information of their location is still stored in the application's configuration files but being unable to locate the files the application does not present them in its history.

Regards.

---

### Post by Lightning Dragon on 2016-04-08
Hello,

His layout is at /home and we have set his external book up to boot from the drives when the laptop is booted with the instructions through the previously mentioned thread to see if that would help (at /media). 

How do I fix it for him so that it does remember? 

Thanks,

---

### Post by Lightning Dragon on 2016-04-10
Hello,

I've tried remounting the device to see if that would help but the result was disappointing. 

Any help?

---

### Post by oldos2er on 2016-04-10
> **Lightning Dragon said:**
> I've tried remounting the device to see if that would help but the result was disappointing. 

We really need specific information, namely from these three commands: ```
sudo blkid

mount

cat /etc/fstab
```

---

### Post by mc4man on 2016-04-10
Picking 2 mentioned that use different & app specific means - 
"Libreoffice will forget documents &  terminal will not remember commands,"

libreoffice keeps recently opened in ~/.config/libreoffice/4/user/registrymodifications.xcu
gnome-terminal keeps in ~/.bash_history
What is the state of these 2 files, both are human readable so open in a text editor & see.

---

### Post by Lightning Dragon on 2016-04-10
Hello, 

I asked him to give the results of the commands, and here is what he got:

Results of blkid
```

/dev/sda1: UUID="53a86476-4ba4-481a-8ae3-5e98ea7181b9" TYPE="ext4" 
/dev/sda5: UUID="99d0a1cf-3e9b-4edb-a62e-6ab542d8a350" TYPE="swap" 
/dev/sdb1: LABEL="College" UUID="7B2GH5692GH31R90" TYPE="ntfs" 
```

Results of mount.
```

/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
/dev/sdb1 on /media/College type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=codeos)
```

Results of cat /etc/fstab

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=53a86476-4ba4-481a-8ae3-5e98ea7181b9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=99d0a1cf-3e9b-4edb-a62e-6ab542d8a350 none            swap    sw              0       0
UUID=7B2GH5692GH31R90 /media/College  ntfs-3g  defaults,uid=1000,windows_names,locale=en_US.utf8  0 0
```

@mc4man

You want what is inside of them? The libre file is pretty huge...but okay. It's permissions seem fine, as well (read and write for codeos (his name)).

```
<?xml version="1.0" encoding="UTF-8"?>
<oor:items xmlns:oor="http://openoffice.org/2001/registry" xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
<item oor:path="/org.openoffice.Office.Common/Misc"><prop oor:name="FirstRun" oor:op="fuse"><value>false</value></prop></item>
<item oor:path="/org.openoffice.Office.Linguistic/ServiceManager/HyphenatorList"><prop oor:name="cs-CZ" oor:op="fuse" oor:type="oor:string-list"><value><it>org.openoffice.lingu.LibHnjHyphenator</it></value></prop></item>
<item oor:path="/org.openoffice.Office.Linguistic/ServiceManager/HyphenatorList"><prop oor:name="da-DK" oor:op="fuse" oor:type="oor:string-list"><value><it>org.openoffice.lingu.LibHnjHyphenator</it></value></prop></item>
<item oor:path="/org.openoffice.Office.Linguistic/ServiceManager/HyphenatorList"><prop oor:name="el-GR" oor:op="fuse" oor:type="oor:string-list"><value><it>org.openoffice.lingu.LibHnjHyphenator</it></value></prop></item>
<item oor:path="/org.openoffice.Office.Linguistic/ServiceManager/HyphenatorList"><prop oor:name="en-CA" oor:op="fuse" oor:type="oor:string-list"><value><it>org.openoffice.lingu.LibHnjHyphenator</it></value></prop></item>
<item oor:path="/org.openoffice.Office.Linguistic/ServiceManager/HyphenatorList"><prop oor:name="en-GB" oor:op="fuse" oor:type="oor:string-list"><value><it>org.openoffice.lingu.LibHnjHyphenator</it></value></prop></item>
<item oor:path="/org.openoffice.Office.Linguistic/ServiceManager/HyphenatorList"><prop oor:name="en-US" oor:op="fuse" oor:type="oor:string-list"><value><it>org.openoffice.lingu.LibHnjHyphenator</it></value></prop></item>
<item oor:path="/org.openoffice.Office.Linguistic/ServiceManager/HyphenatorList"><prop oor:name="es-ES" oor:op="fuse" oor:type="oor:string-list"><value><it>org.openoffice.lingu.LibHnjHyphenator</it></value></prop></item>
<item oor:path="/org.openoffice.Office.Linguistic/ServiceManager/HyphenatorList"><prop oor:name="fi-FI" oor:op="fuse" oor:type="oor:string-list"><value><it>org.openoffice.lingu.LibHnjHyphenator</it></value></prop></item>
<item oor:path="/org.openoffice.Office.Linguistic/ServiceManager/HyphenatorList"><prop oor:name="ga-IE" oor:op="fuse" oor:type="oor:string-list"><value><it>org.openoffice.lingu.LibHnjHyphenator</it></value></prop></item>
<item oor:path="/org.openoffice.Office.Linguistic/ServiceManager/HyphenatorList"><prop oor:name="id-ID" oor:op="fuse" oor:type="oor:string-list"><value><it>org.openoffice.lingu.LibHnjHyphenator</it></value></prop></item>
<item oor:path="/org.openoffice.Office.Linguistic/ServiceManager/HyphenatorList"><prop oor:name="is-IS" oor:op="fuse" oor:type="oor:string-list"><value><it>org.openoffice.lingu.LibHnjHyphenator</it></value></prop></item>
<item oor:path="/org.openoffice.Office.Linguistic/ServiceManager/HyphenatorList"><prop oor:name="nl-NL" oor:op="fuse" oor:type="oor:string-list"><value><it>org.openoffice.lingu.LibHnjHyphenator</it></value></prop></item>
<item oor:path="/org.openoffice.Office.Linguistic/ServiceManager/HyphenatorList"><prop oor:name="pt-BR" oor:op="fuse" oor:type="oor:string-list"><value><it>org.openoffice.lingu.LibHnjHyphenator</it></value></prop></item>
<item oor:path="/org.openoffice.Office.Linguistic/ServiceManager/HyphenatorList"><prop oor:name="pt-PT" oor:op="fuse" oor:type="oor:string-list"><value><it>org.openoffice.lingu.LibHnjHyphenator</it></value></prop></item>
<item oor:path="/org.openoffice.Office.Linguistic/ServiceManager/HyphenatorList"><prop oor:name="sk-SK" oor:op="fuse" oor:type="oor:string-list"><value><it>org.openoffice.lingu.LibHnjHyphenator</it></value></prop></item>
<item oor:path="/org.openoffice.Office.Linguistic/ServiceManager/HyphenatorList"><prop oor:name="uk-UA" oor:op="fuse" oor:type="oor:string-list"><value><it>org.openoffice.lingu.LibHnjHyphenator</it></value></prop></item>
<item oor:path="/org.openoffice.Office.Linguistic/ServiceManager/LastFoundHyphenators"><prop oor:name="cs-CZ" oor:op="fuse" oor:type="oor:string-list"><value><it>org.openoffice.lingu.LibHnjHyphenator</it></value></prop></item>
<item oor:path="/org.openoffice.Office.Linguistic/ServiceManager/LastFoundHyphenators"><prop oor:name="da-DK" oor:op="fuse" oor:type="oor:string-list"><value><it>org.openoffice.lingu.LibHnjHyphenator</it></value></prop></item>
<item oor:path="/org.openoffice.Office.Linguistic/ServiceManager/LastFoundHyphenators"><prop oor:name="el-GR" oor:op="fuse" oor:type="oor:string-list"><value><it>org.openoffice.lingu.LibHnjHyphenator</it></value></prop></item>
<item oor:path="/org.openoffice.Office.Linguistic/ServiceManager/LastFoundHyphenators"><prop oor:name="en-CA" oor:op="fuse" oor:type="oor:string-list"><value><it>org.openoffice.lingu.LibHnjHyphenator</it></value></prop></item>
<item oor:path="/org.openoffice.Office.Linguistic/ServiceManager/LastFoundHyphenators"><prop oor:name="en-GB" oor:op="fuse" oor:type="oor:string-list"><value><it>org.openoffice.lingu.LibHnjHyphenator</it></value></prop></item>
<item oor:path="/org.openoffice.Office.Linguistic/ServiceManager/LastFoundHyphenators"><prop oor:name="en-US" oor:op="fuse" oor:type="oor:string-list"><value><it>org.openoffice.lingu.LibHnjHyphenator</it></value></prop></item>
<item oor:path="/org.openoffice.Office.Linguistic/ServiceManager/LastFoundHyphenators"><prop oor:name="es-ES" oor:op="fuse" oor:type="oor:string-list"><value><it>org.openoffice.lingu.LibHnjHyphenator</it></value></prop></item>
<item oor:path="/org.openoffice.Office.Linguistic/ServiceManager/LastFoundHyphenators"><prop oor:name="fi-FI" oor:op="fuse" oor:type="oor:string-list"><value><it>org.openoffice.lingu.LibHnjHyphenator</it></value></prop></item>
<item oor:path="/org.openoffice.Office.Linguistic/ServiceManager/LastFoundHyphenators"><prop oor:name="ga-IE" oor:op="fuse" oor:type="oor:string-list"><value><it>org.openoffice.lingu.LibHnjHyphenator</it></value></prop></item>
<item oor:path="/org.openoffice.Office.Linguistic/ServiceManager/LastFoundHyphenators"><prop oor:name="id-ID" oor:op="fuse" oor:type="oor:string-list"><value><it>org.openoffice.lingu.LibHnjHyphenator</it></value></prop></item>
<item oor:path="/org.openoffice.Office.Linguistic/ServiceManager/LastFoundHyphenators"><prop oor:name="is-IS" oor:op="fuse" oor:type="oor:string-list"><value><it>org.openoffice.lingu.LibHnjHyphenator</it></value></prop></item>
<item oor:path="/org.openoffice.Office.Linguistic/ServiceManager/LastFoundHyphenators"><prop oor:name="nl-NL" oor:op="fuse" oor:type="oor:string-list"><value><it>org.openoffice.lingu.LibHnjHyphenator</it></value></prop></item>
<item oor:path="/org.openoffice.Office.Linguistic/ServiceManager/LastFoundHyphenators"><prop oor:name="pt-BR" oor:op="fuse" oor:type="oor:string-list"><value><it>org.openoffice.lingu.LibHnjHyphenator</it></value></prop></item>
<item oor:path="/org.openoffice.Office.Linguistic/ServiceManager/LastFoundHyphenators"><prop oor:name="pt-PT" oor:op="fuse" oor:type="oor:string-list"><value><it>org.openoffice.lingu.LibHnjHyphenator</it></value></prop></item>
<item oor:path="/org.openoffice.Office.Linguistic/ServiceManager/LastFoundHyphenators"><prop oor:name="sk-SK" oor:op="fuse" oor:type="oor:string-list"><value><it>org.openoffice.lingu.LibHnjHyphenator</it></value></prop></item>
<item oor:path="/org.openoffice.Office.Linguistic/ServiceManager/LastFoundHyphenators"><prop oor:name="uk-UA" oor:op="fuse" oor:type="oor:string-list"><value><it>org.openoffice.lingu.LibHnjHyphenator</it></value></prop></item>
<item oor:path="/org.openoffice.Office.Linguistic/ServiceManager/LastFoundSpellCheckers"><prop oor:name="en-AU" oor:op="fuse" oor:type="oor:string-list"><value><it>org.openoffice.lingu.MySpellSpellChecker</it></value></prop></item>
<item oor:path="/org.openoffice.Office.Linguistic/ServiceManager/LastFoundSpellCheckers"><prop oor:name="en-GB" oor:op="fuse" oor:type="oor:string-list"><value><it>org.openoffice.lingu.MySpellSpellChecker</it></value></prop></item>
<item oor:path="/org.openoffice.Office.Linguistic/ServiceManager/LastFoundSpellCheckers"><prop oor:name="en-US" oor:op="fuse" oor:type="oor:string-list"><value><it>org.openoffice.lingu.MySpellSpellChecker</it></value></prop></item>
<item oor:path="/org.openoffice.Office.Linguistic/ServiceManager/LastFoundSpellCheckers"><prop oor:name="en-ZA" oor:op="fuse" oor:type="oor:string-list"><value><it>org.openoffice.lingu.MySpellSpellChecker</it></value></prop></item>
<item oor:path="/org.openoffice.Office.Linguistic/ServiceManager/LastFoundThesauri"><prop oor:name="en-US" oor:op="fuse" oor:type="oor:string-list"><value><it>org.openoffice.lingu.new.Thesaurus</it></value></prop></item>
<item oor:path="/org.openoffice.Office.Linguistic/ServiceManager/SpellCheckerList"><prop oor:name="en-AU" oor:op="fuse" oor:type="oor:string-list"><value><it>org.openoffice.lingu.MySpellSpellChecker</it></value></prop></item>
<item oor:path="/org.openoffice.Office.Linguistic/ServiceManager/SpellCheckerList"><prop oor:name="en-GB" oor:op="fuse" oor:type="oor:string-list"><value><it>org.openoffice.lingu.MySpellSpellChecker</it></value></prop></item>
<item oor:path="/org.openoffice.Office.Linguistic/ServiceManager/SpellCheckerList"><prop oor:name="en-US" oor:op="fuse" oor:type="oor:string-list"><value><it>org.openoffice.lingu.MySpellSpellChecker</it></value></prop></item>
<item oor:path="/org.openoffice.Office.Linguistic/ServiceManager/SpellCheckerList"><prop oor:name="en-ZA" oor:op="fuse" oor:type="oor:string-list"><value><it>org.openoffice.lingu.MySpellSpellChecker</it></value></prop></item>
<item oor:path="/org.openoffice.Office.Linguistic/ServiceManager/ThesaurusList"><prop oor:name="en-US" oor:op="fuse" oor:type="oor:string-list"><value><it>org.openoffice.lingu.new.Thesaurus</it></value></prop></item>
<item oor:path="/org.openoffice.Office.Recovery/RecoveryInfo"><prop oor:name="SessionData" oor:op="fuse"><value>false</value></prop></item>
<item oor:path="/org.openoffice.Office.Recovery/RecoveryList"><node oor:name="recovery_item_1" oor:op="remove"/></item>
<item oor:path="/org.openoffice.Office.UI.WriterWindowState/UIElements/States/org.openoffice.Office.UI.WindowState:WindowStateType['private:resource/toolbar/standardbar']"><prop oor:name="ContextActive" oor:op="fuse"><value>true</value></prop></item>
<item oor:path="/org.openoffice.Office.UI.WriterWindowState/UIElements/States/org.openoffice.Office.UI.WindowState:WindowStateType['private:resource/toolbar/standardbar']"><prop oor:name="ContextSensitive" oor:op="fuse"><value>true</value></prop></item>
<item oor:path="/org.openoffice.Office.UI.WriterWindowState/UIElements/States/org.openoffice.Office.UI.WindowState:WindowStateType['private:resource/toolbar/standardbar']"><prop oor:name="DockPos" oor:op="fuse"><value>0,0</value></prop></item>
<item oor:path="/org.openoffice.Office.UI.WriterWindowState/UIElements/States/org.openoffice.Office.UI.WindowState:WindowStateType['private:resource/toolbar/standardbar']"><prop oor:name="Docked" oor:op="fuse"><value>true</value></prop></item>
<item oor:path="/org.openoffice.Office.UI.WriterWindowState/UIElements/States/org.openoffice.Office.UI.WindowState:WindowStateType['private:resource/toolbar/standardbar']"><prop oor:name="DockingArea" oor:op="fuse"><value>0</value></prop></item>
<item oor:path="/org.openoffice.Office.UI.WriterWindowState/UIElements/States/org.openoffice.Office.UI.WindowState:WindowStateType['private:resource/toolbar/standardbar']"><prop oor:name="HideFromToolbarMenu" oor:op="fuse"><value>false</value></prop></item>
<item oor:path="/org.openoffice.Office.UI.WriterWindowState/UIElements/States/org.openoffice.Office.UI.WindowState:WindowStateType['private:resource/toolbar/standardbar']"><prop oor:name="Locked" oor:op="fuse"><value>false</value></prop></item>
<item oor:path="/org.openoffice.Office.UI.WriterWindowState/UIElements/States/org.openoffice.Office.UI.WindowState:WindowStateType['private:resource/toolbar/standardbar']"><prop oor:name="NoClose" oor:op="fuse"><value>false</value></prop></item>
<item oor:path="/org.openoffice.Office.UI.WriterWindowState/UIElements/States/org.openoffice.Office.UI.WindowState:WindowStateType['private:resource/toolbar/standardbar']"><prop oor:name="Pos" oor:op="fuse"><value>2147483647,2147483647</value></prop></item>
<item oor:path="/org.openoffice.Office.UI.WriterWindowState/UIElements/States/org.openoffice.Office.UI.WindowState:WindowStateType['private:resource/toolbar/standardbar']"><prop oor:name="Size" oor:op="fuse"><value>0,0</value></prop></item>
<item oor:path="/org.openoffice.Office.UI.WriterWindowState/UIElements/States/org.openoffice.Office.UI.WindowState:WindowStateType['private:resource/toolbar/standardbar']"><prop oor:name="SoftClose" oor:op="fuse"><value>false</value></prop></item>
<item oor:path="/org.openoffice.Office.UI.WriterWindowState/UIElements/States/org.openoffice.Office.UI.WindowState:WindowStateType['private:resource/toolbar/standardbar']"><prop oor:name="Style" oor:op="fuse"><value>0</value></prop></item>
<item oor:path="/org.openoffice.Office.UI.WriterWindowState/UIElements/States/org.openoffice.Office.UI.WindowState:WindowStateType['private:resource/toolbar/standardbar']/UIName"><value xml:lang="en-US">Standard</value></item>
<item oor:path="/org.openoffice.Office.UI.WriterWindowState/UIElements/States/org.openoffice.Office.UI.WindowState:WindowStateType['private:resource/toolbar/standardbar']"><prop oor:name="Visible" oor:op="fuse"><value>true</value></prop></item>
<item oor:path="/org.openoffice.Office.UI.WriterWindowState/UIElements/States/org.openoffice.Office.UI.WindowState:WindowStateType['private:resource/toolbar/textobjectbar']"><prop oor:name="ContextActive" oor:op="fuse"><value>true</value></prop></item>
<item oor:path="/org.openoffice.Office.UI.WriterWindowState/UIElements/States/org.openoffice.Office.UI.WindowState:WindowStateType['private:resource/toolbar/textobjectbar']"><prop oor:name="ContextSensitive" oor:op="fuse"><value>true</value></prop></item>
<item oor:path="/org.openoffice.Office.UI.WriterWindowState/UIElements/States/org.openoffice.Office.UI.WindowState:WindowStateType['private:resource/toolbar/textobjectbar']"><prop oor:name="DockPos" oor:op="fuse"><value>0,1</value></prop></item>
<item oor:path="/org.openoffice.Office.UI.WriterWindowState/UIElements/States/org.openoffice.Office.UI.WindowState:WindowStateType['private:resource/toolbar/textobjectbar']"><prop oor:name="Docked" oor:op="fuse"><value>true</value></prop></item>
<item oor:path="/org.openoffice.Office.UI.WriterWindowState/UIElements/States/org.openoffice.Office.UI.WindowState:WindowStateType['private:resource/toolbar/textobjectbar']"><prop oor:name="DockingArea" oor:op="fuse"><value>0</value></prop></item>
<item oor:path="/org.openoffice.Office.UI.WriterWindowState/UIElements/States/org.openoffice.Office.UI.WindowState:WindowStateType['private:resource/toolbar/textobjectbar']"><prop oor:name="HideFromToolbarMenu" oor:op="fuse"><value>false</value></prop></item>
<item oor:path="/org.openoffice.Office.UI.WriterWindowState/UIElements/States/org.openoffice.Office.UI.WindowState:WindowStateType['private:resource/toolbar/textobjectbar']"><prop oor:name="Locked" oor:op="fuse"><value>false</value></prop></item>
<item oor:path="/org.openoffice.Office.UI.WriterWindowState/UIElements/States/org.openoffice.Office.UI.WindowState:WindowStateType['private:resource/toolbar/textobjectbar']"><prop oor:name="NoClose" oor:op="fuse"><value>false</value></prop></item>
<item oor:path="/org.openoffice.Office.UI.WriterWindowState/UIElements/States/org.openoffice.Office.UI.WindowState:WindowStateType['private:resource/toolbar/textobjectbar']"><prop oor:name="Pos" oor:op="fuse"><value>2147483647,2147483647</value></prop></item>
<item oor:path="/org.openoffice.Office.UI.WriterWindowState/UIElements/States/org.openoffice.Office.UI.WindowState:WindowStateType['private:resource/toolbar/textobjectbar']"><prop oor:name="Size" oor:op="fuse"><value>0,0</value></prop></item>
<item oor:path="/org.openoffice.Office.UI.WriterWindowState/UIElements/States/org.openoffice.Office.UI.WindowState:WindowStateType['private:resource/toolbar/textobjectbar']"><prop oor:name="SoftClose" oor:op="fuse"><value>false</value></prop></item>
<item oor:path="/org.openoffice.Office.UI.WriterWindowState/UIElements/States/org.openoffice.Office.UI.WindowState:WindowStateType['private:resource/toolbar/textobjectbar']"><prop oor:name="Style" oor:op="fuse"><value>0</value></prop></item>
<item oor:path="/org.openoffice.Office.UI.WriterWindowState/UIElements/States/org.openoffice.Office.UI.WindowState:WindowStateType['private:resource/toolbar/textobjectbar']/UIName"><value xml:lang="en-US">Formatting</value></item>
<item oor:path="/org.openoffice.Office.UI.WriterWindowState/UIElements/States/org.openoffice.Office.UI.WindowState:WindowStateType['private:resource/toolbar/textobjectbar']"><prop oor:name="Visible" oor:op="fuse"><value>true</value></prop></item>
<item oor:path="/org.openoffice.Office.Views/Windows"><node oor:name="SplitWindow0" oor:op="replace"><node oor:name="UserData"><prop oor:name="UserItem" oor:op="fuse" oor:type="xs:string"><value>V1,2,0</value></prop></node><prop oor:name="Visible" oor:op="fuse"><value xsi:nil="true"/></prop><prop oor:name="WindowState" oor:op="fuse"><value xsi:nil="true"/></prop></node></item>
<item oor:path="/org.openoffice.Office.Views/Windows"><node oor:name="SplitWindow1" oor:op="replace"><node oor:name="UserData"><prop oor:name="UserItem" oor:op="fuse" oor:type="xs:string"><value>V1,2,0</value></prop></node><prop oor:name="Visible" oor:op="fuse"><value xsi:nil="true"/></prop><prop oor:name="WindowState" oor:op="fuse"><value xsi:nil="true"/></prop></node></item>
<item oor:path="/org.openoffice.Office.Views/Windows"><node oor:name="SplitWindow2" oor:op="replace"><node oor:name="UserData"><prop oor:name="UserItem" oor:op="fuse" oor:type="xs:string"><value>V1,2,0</value></prop></node><prop oor:name="Visible" oor:op="fuse"><value xsi:nil="true"/></prop><prop oor:name="WindowState" oor:op="fuse"><value xsi:nil="true"/></prop></node></item>
<item oor:path="/org.openoffice.Office.Views/Windows"><node oor:name="SplitWindow3" oor:op="replace"><node oor:name="UserData"><prop oor:name="UserItem" oor:op="fuse" oor:type="xs:string"><value>V1,2,0</value></prop></node><prop oor:name="Visible" oor:op="fuse"><value xsi:nil="true"/></prop><prop oor:name="WindowState" oor:op="fuse"><value xsi:nil="true"/></prop></node></item>
<item oor:path="/org.openoffice.Office.Views/Windows"><node oor:name="swriter/10365" oor:op="replace"><node oor:name="UserData"><prop oor:name="Data" oor:op="fuse" oor:type="xs:string"><value>V2,V,128</value></prop></node><prop oor:name="Visible" oor:op="fuse"><value xsi:nil="true"/></prop><prop oor:name="WindowState" oor:op="fuse"><value></value></prop></node></item>
<item oor:path="/org.openoffice.Office.Writer/Layout/Line"><prop oor:name="Guide" oor:op="fuse"><value>false</value></prop></item>
<item oor:path="/org.openoffice.Office.Writer/Layout/Other"><prop oor:name="ApplyCharUnit" oor:op="fuse"><value>true</value></prop></item>
<item oor:path="/org.openoffice.Office.Writer/Layout/Other"><prop oor:name="IsAlignMathObjectsToBaseline" oor:op="fuse"><value>true</value></prop></item>
<item oor:path="/org.openoffice.Office.Writer/Layout/Other"><prop oor:name="IsSquaredPageMode" oor:op="fuse"><value>true</value></prop></item>
<item oor:path="/org.openoffice.Office.Writer/Layout/Other"><prop oor:name="MeasureUnit" oor:op="fuse"><value>8</value></prop></item>
<item oor:path="/org.openoffice.Office.Writer/Layout/Other"><prop oor:name="TabStop" oor:op="fuse"><value>1251</value></prop></item>
<item oor:path="/org.openoffice.Office.Writer/Layout/ViewLayout"><prop oor:name="BookMode" oor:op="fuse"><value>false</value></prop></item>
<item oor:path="/org.openoffice.Office.Writer/Layout/ViewLayout"><prop oor:name="Columns" oor:op="fuse"><value>0</value></prop></item>
<item oor:path="/org.openoffice.Office.Writer/Layout/Window"><prop oor:name="HorizontalRuler" oor:op="fuse"><value>true</value></prop></item>
<item oor:path="/org.openoffice.Office.Writer/Layout/Window"><prop oor:name="HorizontalRulerUnit" oor:op="fuse"><value xsi:nil="true"/></prop></item>
<item oor:path="/org.openoffice.Office.Writer/Layout/Window"><prop oor:name="HorizontalScroll" oor:op="fuse"><value>true</value></prop></item>
<item oor:path="/org.openoffice.Office.Writer/Layout/Window"><prop oor:name="IsVerticalRulerRight" oor:op="fuse"><value>false</value></prop></item>
<item oor:path="/org.openoffice.Office.Writer/Layout/Window"><prop oor:name="ShowRulers" oor:op="fuse"><value>true</value></prop></item>
<item oor:path="/org.openoffice.Office.Writer/Layout/Window"><prop oor:name="ShowScrollBarTips" oor:op="fuse"><value>true</value></prop></item>
<item oor:path="/org.openoffice.Office.Writer/Layout/Window"><prop oor:name="SmoothScroll" oor:op="fuse"><value>false</value></prop></item>
<item oor:path="/org.openoffice.Office.Writer/Layout/Window"><prop oor:name="VerticalRuler" oor:op="fuse"><value>true</value></prop></item>
<item oor:path="/org.openoffice.Office.Writer/Layout/Window"><prop oor:name="VerticalRulerUnit" oor:op="fuse"><value xsi:nil="true"/></prop></item>
<item oor:path="/org.openoffice.Office.Writer/Layout/Window"><prop oor:name="VerticalScroll" oor:op="fuse"><value>true</value></prop></item>
<item oor:path="/org.openoffice.Office.Writer/Layout/Zoom"><prop oor:name="Type" oor:op="fuse"><value>0</value></prop></item>
<item oor:path="/org.openoffice.Office.Writer/Layout/Zoom"><prop oor:name="Value" oor:op="fuse"><value>100</value></prop></item>
<item oor:path="/org.openoffice.Setup/L10N"><prop oor:name="ooLocale" oor:op="fuse"><value>en-US</value></prop></item>
<item oor:path="/org.openoffice.Setup/Office/Factories/org.openoffice.Setup:Factory['com.sun.star.text.TextDocument']"><prop oor:name="ooSetupFactoryWindowAttributes" oor:op="fuse"><value>58,78,1805,980;1;0,0,0,0;</value></prop></item>
<item oor:path="/org.openoffice.Setup/Office"><prop oor:name="LastCompatibilityCheckID" oor:op="fuse"><value>420m0(Build:2)</value></prop></item>
<item oor:path="/org.openoffice.Setup/Office"><prop oor:name="ooSetupInstCompleted" oor:op="fuse"><value>true</value></prop></item>
</oor:items>
```

And the bash_history is empty, with the following permissions: read and write for codeos (his name).

Firefox, Chrome and Gimp seem to have no problem for him though, or even what he searches in the Dash. If that helps to know?



Thanks for the help! :D

---

### Post by mc4man on 2016-04-10
> **Lightning Dragon said:**
> Hello, 


@mc4man

You want what is inside of them? The libre file is pretty huge...but okay. It's permissions seem fine, as well (read and write for codeos (his name)).



And the bash_history is empty, with the following permissions: read and write for codeos (his name).

Firefox, Chrome and Gimp seem to have no problem for him though, or even what he searches in the Dash. If that helps to know?



Thanks for the help! :D
didn't really need to see as it is a potentially large file. History is saved on lines like - 
<item oor:path="/org.openoffice.Office.Histories/Histories/org.openoffice.Office.Histories:HistoryInfo['PickList']/ItemList"><node oor:name="file:///home/doug/Desktop/install-361"  ....ect., ect.

Don't see any.
Curious - what release of Ubuntu did you give him, only asking because in recent history Ubuntu using nautilus would not give the real user name when checking permissions, it would say "Me"
For starters maybe have him delete both bash_history & the libreoffice file

---

### Post by Lightning Dragon on 2016-04-11
Hello,

Oh, sorry. I wasn't sure what part of it you needed, so I just gave the whole thing. And he is using the latest LTS, 14.0.4. Well it does say "me" but in the dropdown "Group" box, it lists his name. I just thought that might have been important to mention. :) 

I had him delete the bash_history and the libreoffice file. It seemed to work for the terminal after a reboot, but still the same for his other applications that load off of the external drive.


Thanks!

---

### Post by oldos2er on 2016-04-11
> **Lightning Dragon said:**
> still the same for his other applications that load off of the external drive.

Is this the /media/College partition? And you're saying that these programs are actually installed somewhere other than / ? Were they installed with the package manager?

---

### Post by Lightning Dragon on 2016-04-11
> **oldos2er said:**
> Is this the /media/College partition? And you're saying that these programs are actually installed somewhere other than / ? Were they installed with the package manager?

Hello,

I just realized how I worded myself there. I meant when the programs are loading items off of the external book @ /media/College. The programs are actually on the laptop drive and the applications can remember things when that item is on the laptop drive, but nothing on external drives that boot up with the machine. All applications were installed either with package manager or with simple terminal commands.

I'm sorry for the wording I used there. 

Thanks!

---

### Post by mc4man on 2016-04-11
The Recent Documents in LO writer will only show recent docs that are available. Ex. - open a doc in writer that's on an external drive. That doc would then show in that menu. Disconnect the drive & it will go away but if the drive is re-connected it will come back.

So do any files opened from the external drive ever show up in Recent ..? Do any files opened from the laptop ever show in Recent ..?
By ever mean ever, ex.,  open a doc in Lo writer, while doc is open ck. the menu, that doc should be listed

Maybe run & check for root ownership on anything - 
```
ls -lA -R  |grep root
```

---

### Post by Lightning Dragon on 2016-04-12
Hello,

The document are definitely available, and even if the drive is disconnected and reconnected, the history is just empty upon checking after reboot. If he leaves the PC on, it remembers the history for everything. 

As for your command, it comes back with lots of results containing "root" in red (positive?), but there were three results that did not match the rest:

ls: cannot open directory ./.cache/dconf: Permission denied

ls: cannot open directory ./.config/enchant: Permission denied

ls: cannot open directory ./.dbus: Permission denied

---

### Post by mc4man on 2016-04-12
> **Lightning Dragon said:**
> Hello,

The document are definitely available, and even if the drive is disconnected and reconnected, the history is just empty upon checking after reboot. If he leaves the PC on, it remembers the history for everything. 

As for your command, it comes back with lots of results containing "root" in red (positive?), but there were three results that did not match the rest:

ls: cannot open directory ./.cache/dconf: Permission denied

ls: cannot open directory ./.config/enchant: Permission denied

ls: cannot open directory ./.dbus: Permission denied
As far as the ls command you only needed to be concerned with any files owned by root, not any files with root in their name.
Just to make obvious here I've lots of files with root in the name but absolutely no root owned files in my home folder. (truncated, blue is owner
> $ ls -lA -R  |grep root
-rw------- 1 [COLOR="#0000CD"]doug doug[/COLOR]   716 Apr 12 13:08 root
-rw-rw-r-- 1 doug doug 32768 Apr 12 13:08 root-2a53aa84.log
-rw-r--r-- 1 doug doug  7864 Jan 31  2015 root.js
-rwxrwxr-x 1 doug doug   19456 Oct  1  2012 mozroots.exe

The existence of .cache/dconf/user &  .dbus/* indicate your friend has been running root commands improperly, like sudo nautilus, sudo gedit, ect.  As far as .config/enchant no idea but it shouldn't be there as root owned.
So as root get rid of all 3 folders & their contents. Plus look over the ls for anything else root owns, if anything

---

### Post by Lightning Dragon on 2016-04-12
Hello,

Yes, a lot of them were files with the word root in it but some of them were not. 

How do I help him remove those folders correctly? 

Thanks,

---

### Post by mc4man on 2016-04-13
> **Lightning Dragon said:**
> Hello,

Yes, a lot of them were files with the word root in it but some of them were not. 

How do I help him remove those folders correctly? 

Thanks,
Post the results of the ls command or just do a fresh install & advise against using sudo to open applications

---

### Post by Lightning Dragon on 2016-04-25
> **mc4man said:**
> Post the results of the ls command or just do a fresh install & advise against using sudo to open applications


Sorry for the late response. He decided to just do a fresh install with a DVD instead of a USB stick and everything seems to working fine now. :)

---

