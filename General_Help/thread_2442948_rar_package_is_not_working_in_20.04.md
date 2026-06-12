---
title: "rar package is not working in 20.04"
date: 2020-05-09
forum: General Help
---

### Post by makem2 on 2020-05-09
I have installed the rar and unrar packages from the repos and find that what I attempt to create a rar archive I get an error, "Failed to create archive. No suitable archive manager found".

I have uninstalled engrampa for the MATE environment which was installed when I installed the OS.  Does rar depend on this?

---

### Post by CelticWarrior on 2020-05-09
It does depend on something if the goal is to be used in GUI.

---

### Post by makem2 on 2020-05-09
I removed engrampa was because I was having problems extracting a rar.

I would select a rar file which was passworded, be asked for the location for the extraction to take place and then the password. When I selected 'OK' nothing was extracted.

I have reinstalled engampa and can again make a rar file. However, I still get the problem of not being able to extract it to a location. I can extract it to 'Here'.
Does unrar depend on something other than engrampa?

I have never had this problem in any other version of xubuntu. In fact I have never needed to instal unrar before.

---

### Post by CelticWarrior on 2020-05-09
I think the problem is the *where*, not the *what* or *how*.
Do you have write permissions to where you're trying to extract the file(s)?

---

### Post by pqwoerituytrueiwoq on 2020-05-09
rar files work fine for me on xubuntu 20.04 (not a clean install)
here are the packages i have installed
[https://i.imgur.com/n0lcHzK.png](https://i.imgur.com/n0lcHzK.png)
I am able to create, open, and extract rar files just fine using the GUI

There used to be a bug (not sure if it got patched) where files would be decompressed in the same directory as the archive is located instead of the destination of the extraction, if there is insufficient space or no write permission where the archive is it will fail to extract

---

### Post by makem2 on 2020-05-09
> **CelticWarrior said:**
> I think the problem is the *where*, not the *what* or *how*.
Do you have write permissions to where you're trying to extract the file(s)?

That was the first thing I thought of even though I was extracting to a test folder I had created on my desktop. The permissions on that folder are drwxrwxrwx

---

### Post by makem2 on 2020-05-09
> **pqwoerituytrueiwoq said:**
> rar files work fine for me on xubuntu 20.04 (not a clean install)
here are the packages i have installed
[https://i.imgur.com/n0lcHzK.png](https://i.imgur.com/n0lcHzK.png)
I am able to create, open, and extract rar files just fine using the GUI

There used to be a bug (not sure if it got patched) where files would be decompressed in the same directory as the archive is located instead of the destination of the extraction, if there is insufficient space or no write permission where the archive is it will fail to extract

I don't have file-roller, libarchive-zip-perl, lignome-autoar-gtk-0-0, perl-modules-5.24 and 5.26 unzip, zip.

I do have perl-modules-5.30

As a matter of interest, how do you get all relevant packages to list together? When I choose 'archive' as search criteria my list is all over the place and I need to scroll through the list to find each one.

---

### Post by makem2 on 2020-05-09
It seems I can only extract to the directory the rar is in, or to a folder within the directory of the rar is in.

If I try to extract anywhere else such as 'downloads' I don't get any output.

Very strange, I am the owner of all files concerned.

---

### Post by makem2 on 2020-05-09
> **pqwoerituytrueiwoq said:**
> rar files work fine for me on xubuntu 20.04 (not a clean install)
here are the packages i have installed
[https://i.imgur.com/n0lcHzK.png](https://i.imgur.com/n0lcHzK.png)
I am able to create, open, and extract rar files just fine using the GUI

There used to be a bug (not sure if it got patched) where files would be decompressed in the same directory as the archive is located instead of the destination of the extraction, if there is insufficient space or no write permission where the archive is it will fail to extract

I now have all the packages you have except for:

```

makem@XPS-13-9300:~$ sudo apt-get install perl-modules-5.24
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package perl-modules-5.24
E: Couldn't find any package by glob 'perl-modules-5.24'
E: Couldn't find any package by regex 'perl-modules-5.24'
makem@XPS-13-9300:~$ sudo apt-get install perl-modules-5.26
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package perl-modules-5.26
E: Couldn't find any package by glob 'perl-modules-5.26'
E: Couldn't find any package by regex 'perl-modules-5.26'
makem@XPS-13-9300:~$

```

```

makem@XPS-13-9300:/mnt$ ls -la
total 8
drwxr-xr-x  3 root root 4096 May  9 18:19 .
drwxr-xr-x 20 root root 4096 May  6 01:46 ..
drwxrwxrwt  2 root root   40 May  9 21:25 ramdisk
makem@XPS-13-9300:/mnt$ 

```

ramdisk is owned by root but I can write to it from file manager. 

In my 18.04 xubuntu ramdisk is also owned by root and I don't have any problems extracting files to it.


I still cannot extract outside of the folder containing the rar in 20.04.

---

### Post by makem2 on 2020-05-09
Using the terminal I am able to extract:

```

makem@XPS-13-9300:~/Desktop$ unrar e NewFolder.rar /mnt/ramdisk

UNRAR 5.61 beta 1 freeware      Copyright (c) 1993-2018 Alexander Roshal


Extracting from NewFolder.rar

Enter password (will not be echoed) for NewFolder/1.txt: 

Extracting  /mnt/ramdisk/1.txt                                        OK 
NewFolder/2.txt - use current password ? [Y]es, [N]o, [A]ll a

Extracting  /mnt/ramdisk/2.txt                                        OK 
Extracting  /mnt/ramdisk/3.txt                                        OK 
All OK
makem@XPS-13-9300:~/Desktop$ 

```

But I cannot repeat using File Manager.

So permissions must be correct. Could there be a bug?

---

### Post by pqwoerituytrueiwoq on 2020-05-09
My perl-modules-5.24 and perl-modules-5.26 packages are left over after upgrading form older versions of xubuntu, i have a perl-modules-5.30 installed for focal, not sure why those where not auto-removed during the upgrade process
The quick filter feature is not the same as search, i have it sorted my installed stats (click column heading)
here is what i have installed for the file manager [https://imgur.com/HDuiRBq.png](https://imgur.com/HDuiRBq.png)
i do not see anything set to use file-roller (left over from past xubuntu version)

---

### Post by makem2 on 2020-05-10
Thank you for taking the time to assist @[URL="https://ubuntuforums.org/member.php?u=865458"][COLOR=#000000]pqwoerituytrueiwoq

[/COLOR][/URL] We have almost identical packages installed but the inability to extract  to a folder outside the one the rar is in still exists. I want to  extract a rar file to a ramdisk which has been so simple in the past.

All I can think of now is permissions. Will you post the permissions for the file you extract and the folder to which it is extracted to enable me to compare?

---

### Post by makem2 on 2020-05-10
I have uninstalled engrampa but not fully this time and archive manager extracts correctly. It was never a rar problem.

---

### Post by Yellow Pasque on 2020-05-10
Does behavior change if you install p7zip-rar?

---

### Post by makem2 on 2020-05-11
Thanks but I have got it working now so best leave it alone.

---

### Post by pqwoerituytrueiwoq on 2020-05-11
What solved the issue? i have seen more than 1 person with this issue

---

### Post by makem2 on 2020-05-11
> **pqwoerituytrueiwoq said:**
> What solved the issue? i have seen more than 1 person with this issue

I don't really know, however these are the steps I remember having tried so many ways.

1. I uninstalled engrampa because I felt it may be the problem. I selected a complete uninstall. That did not work and I reinstalled it.

2. I followed the packages that you had installed but again even though we had identical packages except for a couple of ones you had from earlier.

3. I again uninstalled engrampa and installed xarchiver. This now worked and I could now extract from a desktop folder to a ramdisk folder or anywhere. I also had the option of extracting with archive manager which I didn't remember seeing in 20.04 before although I was using it in 18.04

4. Uninstalled xarchiver

I now have just the one archive manager, 'Archive Manager' in the right click options and it works fine.

Many thanks for your assistance and the pointer to Quick Filter in Synaptic.

---

### Post by makem2 on 2020-05-11
> **Yellow Pasque said:**
> Does behavior change if you install p7zip-rar?

p7zip and p7zip-full are both installed but p7zip-rar is not

---

