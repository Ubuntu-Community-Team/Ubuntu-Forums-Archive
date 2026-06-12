---
title: "No longer able to access folder in Windows XP computer"
date: 2015-06-15
forum: General Help
---

### Post by KayeNg on 2015-06-15
Hello guys.  

I have a Windows XP desktop computer with two hard drives , C: and D:  There's a folder in Drive C: called DTM and, using Lubuntu on another computer, I could access the DTM folder using this command:

sudo mount.cifs //192.168.1.110/DTM /home/homet/Desktop/Homet-02/DTM -o user=homet-01

Now I copied the DTM folder from Drive C: onto Drive D: , which has Windows XP also installed in it.  Yes, two hard drives, both Windows XP operating system, don't ask why, long story.  This makes the desktop computer a dual boot system, albeit both Windows XP.

Anyway, if I boot into the Windows XP in Drive D:, and using the Lubuntu system to access the DTM folder in Drive D: by the same command as above, I get this:

"Unable to find suitable address."

To summarize, two drives in the same computer,  Drives C and D.  Both drives have a folder named DTM.  C:\DTM  and D:\DTM   
I can access the folder in C, but cannot access it in D.  

Help please.

Thank you.

---

### Post by nerdtron on 2015-06-15
So you boot in C: windows, you have IP 192.168.1.110, and you have a shared folder named DTM -----> this is good, this is why you can use the mount command on Lubuntu.

So when you boot in D: Windows, you should make sure that you have the IP 192.168.1.110, and you have a shared folder named DTM with the same access permission as it did on the C: Windows.

I'm sorry if this is a bit confusing. I hope you will get it.

---

### Post by KayeNg on 2015-06-17
Thank you for your response Nerdtron. Pinoy ka? I did not change anything, it SHOULD work because the folders are identical and are both shared. I don't know why it doesn't work.

---

### Post by KayeNg on 2015-06-17
Hello, Pinoy ka? Yes it is also shared.  I don't understand why it isn't working.

---

### Post by nerdtron on 2015-06-17
PH team! wohooh!

Anyway, you can try to mount it with verbose mode so we can see the error on mounting
```
sudo mount -v -t cifs //192.168.1.110/DTM /home/homet/Desktop/Homet-02/DTM -o user=homet-01
```
Also if you can try to scan from ubuntu if it can see the windows share from each of the windows in C and D drives.
From ubuntu compare the output of "smbtree" for each windows. (just hit enter, if you are asked for password)
```
smbtree
```
How about windows firewall? have you tried to disable it? or perhaps and antivirus on windows blocking the sharing?

---

### Post by KayeNg on 2015-06-18
I tried this
sudo mount -v -t cifs //192.168.1.110/DTM /home/homet/Desktop/Homet-02/DTM -o user=homet-01

Got this:  
[sudo] password for homet: 
Password for homet-01@//192.168.1.110/DTM: 
mount.cifs kernel mount options: ip=192.168.1.110,unc=\\192.168.1.110\DTM,user=homet-01,pass=********
Unable to find suitable address.

Also tried smbtree:

homet@homet-01:~$ smbtree
Enter homet's password: 
MSHOME
    \\MAIN-01                Main-01
    \\HOMET-03               
    \\HOMET-02               232GB
    \\HOMET-01               homet-01 server (Samba, Ubuntu)
        \\HOMET-01\EPSON-L210-Series    EPSON L210 Series
        \\HOMET-01\print$             Printer Drivers
        \\HOMET-01\IPC$               IPC Service (homet-01 server (Samba, Ubuntu))

---

### Post by nerdtron on 2015-06-18
> homet@homet-01:~$ smbtree
Enter homet's password: 
MSHOME
    \\MAIN-01                Main-01
    \\HOMET-03               
    \\HOMET-02               232GB
    \\HOMET-01               homet-01 server (Samba, Ubuntu)
        \\HOMET-01\EPSON-L210-Series    EPSON L210 Series
        \\HOMET-01\print$             Printer Drivers
        \\HOMET-01\IPC$               IPC Service (homet-01 server (Samba, Ubuntu))

Hhhmmm there's no shared folder named DTM on the network? Can you try to reshare the folder? Try to use other machines (preferably another windows box) and see if it can mount the share. You can also try to mount the windows share using smartphone. If you ave android you can mount a windows share using ES File explorer.

The goal here is to isolate is it just the ubuntu machine that cannot mount the share or all other devices can't mount the share.

---

### Post by KayeNg on 2015-06-18
I have access to the shared DTM folder in the Windows XP system when I'm using Windows 7 on another computer.  
Using ES File Explorer in my Android phone I can also access the shared DTM folder in the Windows XP system.

---

