---
title: "Sending file from SMB share to Bluetooth device doesn't work"
date: 2020-12-17
forum: General Help
---

### Post by random20201219 on 2020-12-17
I can't send a file from an SMB share to a smartphone paired with the computer.

Using Dolphin to copy a file from the SMB drive to the computer via the local network works. 

Sending a file on the computer to a device connected via Bluetooth works as well. 

However, what doesn't work is in Dolphin right-clicking a file on the  SMB drive, and then in the context menu choosing Share > Send via  Bluetooth. I can pick the paired device as receiver, but the transfer  immediately crashes.

If you need any logs to address this problem, I'll be happy to provide them.

---

### Post by SeijiSensei on 2020-12-18
Do you have an Android phone? Then try using KDEConnect instead.

Android app here: [https://play.google.com/store/apps/details?id=org.kde.kdeconnect_tp](https://play.google.com/store/apps/details?id=org.kde.kdeconnect_tp)

On the computer you can install it from the repositories with "sudo apt install kdeconnect".

It has other useful features besides sending files. I use Kubuntu, so it's a native application for me, but I'm pretty sure I've heard of people running ordinary Ubuntu and using KDEConnect.

---

### Post by TheFu on 2020-12-18
There is a gnome3-version **gsconnect**  [https://extensions.gnome.org/extension/1319/gsconnect/](https://extensions.gnome.org/extension/1319/gsconnect/)  Looks tied to Gnome3 DE.
[https://www.omgubuntu.co.uk/2018/11/connect-android-ubuntu-gsconnect](https://www.omgubuntu.co.uk/2018/11/connect-android-ubuntu-gsconnect)  updated Aug 2020.

---

### Post by random20201219 on 2020-12-19
Why doesn't the method work that the OS provides out of the box?

---

### Post by TheFu on 2020-12-19
> **hellhound143 said:**
> Why doesn't the method work that the OS provides out of the box?

A guess: Lots of moving parts, mostly created by volunteers, working for free?
[https://arstechnica.com/information-technology/2020/10/google-and-intel-warn-of-high-severity-bluetooth-security-bug-in-linux/](https://arstechnica.com/information-technology/2020/10/google-and-intel-warn-of-high-severity-bluetooth-security-bug-in-linux/) 
Linux has been patched for this problem. Has your Android device?

Bluetooth will never be as fast as wifi, so most people just use wifi to transfer files.
[https://askubuntu.com/questions/626941/how-to-access-my-androids-files-using-wi-fi-in-ubuntu](https://askubuntu.com/questions/626941/how-to-access-my-androids-files-using-wi-fi-in-ubuntu) says to use wifi and to run SSHelper on Android. It is a GPL program.  Then you can use almost any Linux file browser to drag-n-drop files to/from Linux to/from android.  Probably only want to run SSHelper when you need that network connection.  I've not used it, but will probably check it out soon ... added to my list of stuff-to-do the week after Xmas.  There are at least 5 other GPL ssh-servers for android.  In your file manager, a URL like sftp://{username}@{IP address}/ should make a connection assuming you've installed the ssh-client onto your Ubuntu system.  I think it should be there by default in current desktop Ubuntu systems.  Some file managers want ssh:// instead and others want fish:// ... so a quick check for what yours wants - or just try those 3 and get lucky.  ssh/sftp/scp/rsync are how Unix systems communicate between each other securely.

As for SMB not working ... there are two different projects on that.  Microsoft has been changing defaults in Win10 to improve security.  The Apache Samba project has been changing their defaults to improve security as well, but with slightly different needs.  Sometimes these projects don't get the message from the other and things break. 

We are way, way, outside my area here and I know these aren't the options you wanted. Sorry. Maybe someone else can be more help?

---

### Post by random20201219 on 2020-12-19
What has that bug to do with the problem at hand? Or Bluetooth's speed? But I get your answer: if you expect things to work, get a professional OS.

---

### Post by TheFu on 2020-12-19
> **hellhound143 said:**
> What has that bug to do with the problem at hand? Or Bluetooth's speed? But I get your answer: if you expect things to work, get a professional OS.

Not quite my statement, but fine. Linux distros have a tough job herding cats.  The way to get the most trouble-free use from any OS is to 
[LIST]
[*]use things that are well used, 
[*]well tested, 
[*]by the lots of users, 
[*]on the hardware lots of users have, 
[*]in the way most people use it.
[/LIST]
As individuals, where we can have the most impact is to run pre-release versions of the OS, test them for issues important to us, provide that feedback in the way to be helpful. The next release is 21.04 in a few months.  There is a pre-release build of it available.  Donating some testing time is one of the most effective things we can do. [https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed)

Just to clarify. Nobody here works for Canonical. Feel free to ignore me.

---

