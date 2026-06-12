---
title: "Tar File"
date: 2014-03-16
forum: General Help
---

### Post by Sef on 2014-03-16
I was able to get download [Strife]("http://strife.com/"); however, it came as a tar package, and I have not opened one in so long that installing it has proven to be rather frustrating.

What I have accomplished so far:

1) Extracted the package
2) set up a directory named Strife

However, i cannot get to the Strife directory.

What should I do?


Thank you in advance.

---

### Post by dniMretsaM on 2014-03-16
How did you extract the package? What error are you getting when you cd into the strife directory? What are the permissions on the downloaded archive and extracted folder?

---

### Post by Sef on 2014-03-16
> [COLOR=#000000]How did you extract the package?[/COLOR]

Right clicked and used extract.

> [COLOR=#000000]What error are you getting when you cd into the strife directory?[/COLOR]

sef@sef-laptop:~$ cd /home/sef/StrifeClientLinux64-0.0.1.12
bash: cd: /home/sef/StrifeClientLinux64-0.0.1.12: No such file or directory
sef@sef-laptop:~$ /home/StrifeClientLinux64-0.0.1.12
bash: /home/StrifeClientLinux64-0.0.1.12: No such file or directory
sef@sef-laptop:~$ /home/Downloads/StrifeClientLinux64-0.0.1.12
bash: /home/Downloads/StrifeClientLinux64-0.0.1.12: No such file or directory

The folder I created is in /Downloads.  

> [COLOR=#000000]What are the permissions on the downloaded archive and extracted folder?[/COLOR]

Owner: Create and delete files.  (I am the owner.)

Group: Access files

Other: Access files.

---

### Post by deadflowr on 2014-03-16
Maybe
```
ls Downloads
```
if it was extracted to the downloads folder.
Perhaps a name change is the reason it doesn't exit(?).

Just a thought.

---

### Post by Sef on 2014-03-16
> [COLOR=#000000]Perhaps a name change is the reason it doesn't exit(?).[/COLOR]

drwxr-xr-x 6 sef sef       4096 Feb 19 13:48 StrifeClient
drwxr-xr-x 2 sef sef       4096 Mar 16 09:52 StrifeClientLinux64-0.0.1.12
-rw-r--r-- 1 sef sef 1261975527 Mar 12 12:39 StrifeClientLinux64-0.0.1.12.tar.gz

The first two (StrifeClient) are highlighted in light blue, while the third one (StrifeClient) is highlighted

---

### Post by coldcritter64 on 2014-03-16
> sef@sef-laptop:~$ cd **/home/sef/StrifeClientLinux64-0.0.1.12**
bash: cd: /home/sef/StrifeClientLinux64-0.0.1.12: No such file or directory
sef@sef-laptop:~$ **/home/StrifeClientLinux64-0.0.1.12**
bash: /home/StrifeClientLinux64-0.0.1.12: No such file or directory
sef@sef-laptop:~$ **/home/Downloads**/StrifeClientLinux64-0.0.1.12
bash: /home/Downloads/StrifeClientLinux64-0.0.1.12: No such file or directory

The folder I created **is in /Downloads**.  The Downloads folder in Ubuntu is usually at the location /home/<user>/Downloads

Try cd'ing into the folder /home/**sef**/Downloads/StrifeClientLinux64-0.0.1.12 and see if you get an error.

Edit: also, you forgot the "cd" before the last two addresses above.

---

### Post by Sef on 2014-03-16
> [COLOR=#000000]Try cd'ing into the folder /home/[/COLOR]**sef/Downloads/StrifeClientLinux64-0.0.1.12 and see if you get an error.**

Got that part done. Thank you.
 
Now for unpacking the tar file.

---

### Post by coldcritter64 on 2014-03-16
> **Sef said:**
> Got that part done. Thank you.
 
Now for unpacking the tar file.

If you've extracted the tar file into the directory there should be a README or INSTALL file in the contents with specific build/installation notes. Usually you would "configure" a package then "make" or "make install" the package. 

Look for specific instructions, if there are any, in the tar file contents.

---

### Post by Sef on 2014-03-16
> [COLOR=#000000]If you've extracted the tar file into the directory there should be a README or INSTALL file in the contents with specific build/installation notes. Usually you would "configure" a package then "make" or "make install" the package. [/COLOR]

[COLOR=#000000]Look for specific instructions, if there are any, in the tar file contents.[/COLOR]

Unfortunately, there are no instructions or readme or install files.

---

### Post by deadflowr on 2014-03-16
> **Sef said:**
> Unfortunately, there are no instructions or readme or install files.

I hope this means the extraction went well.

What are the contents, if no install or readme file?

Does the strife site give any hints in their faqs.
Or do they just assume since you run linux you are a tech super genius?

---

### Post by coldcritter64 on 2014-03-16
> **Sef said:**
> Unfortunately, there are no instructions or readme or install files.

No readme or install file is unusual. :confused:  Did you sign up for the beta program shown in the link in your OP ? How/from where, did you download the tarball ? The site just asked me for a beta key to download, so I can't do any checking of the file itself.

---

### Post by Sef on 2014-03-16
> [COLOR=#000000]Did you sign up for the beta program shown in the link in your OP ? How/from where, did you download the tarball ? [/COLOR]

I signed up for the beta.

Just downloaded it from the site after installing a beta key.

---

### Post by Yellow Pasque on 2014-03-16
Maybe it's not a directory...
```
file StrifeClientLinux64-0.0.1.12
```
If it's an executable:
```
./StrifeClientLinux64-0.0.1.12
```

---

### Post by Sef on 2014-03-16
I am getting these messages:

sef@sef-laptop:~/Downloads/StrifeClientLinux64-0.0.1.12$ ./StrifeClientLinux64-0.0.1.12
bash: ./StrifeClientLinux64-0.0.1.12: No such file or directory

sef@sef-laptop:~/Downloads/StrifeClientLinux64-0.0.1.12$ file StrifeClientLinux64-0.0.1.12
StrifeClientLinux64-0.0.1.12: ERROR: cannot open `StrifeClientLinux64-0.0.1.12' (No such file or directory)

---

### Post by 3rdalbum on 2014-03-17
Just drag the executable file to the terminal. Don't bother with trying to manually navigate the terminal and type the correct filename. Drag the file to the terminal and hit Enter to run it.

---

### Post by Sef on 2014-03-18
> [COLOR=#000000]Just drag the executable file to the terminal. [/COLOR]


When I drag the bin folder, I get this message:

> sef@sef-laptop:~$ /home/sef/Downloads/StrifeClient/bin
bash: /home/sef/Downloads/StrifeClient/bin: Is a directory
sef@sef-laptop:~$ 


---

### Post by steeldriver on 2014-03-18
> **Sef said:**
> Got that part done. Thank you.
 
Now for unpacking the tar file.

You have already unpacked the tar file (it is the same thing as "extracting the package" - which you did in Post #1)

> **Sef said:**
> drwxr-xr-x 6 sef sef       4096 Feb 19 13:48 StrifeClient
drwxr-xr-x 2 sef sef       4096 Mar 16 09:52 StrifeClientLinux64-0.0.1.12
-rw-r--r-- 1 sef sef 1261975527 Mar 12 12:39 StrifeClientLinux64-0.0.1.12.tar.gz

The first two (StrifeClient) are highlighted in light blue, while the third one (StrifeClient) is highlighted

[LIST]
[*] the first entry ('StrifeClient') is the directory that you created
[*]the second entry ('StrifeClientLinux64-0.0.1.12') is the top-level directory of the (unpacked) tar archive
[*]the third entry is the original gzipped tar file
[/LIST]

Now you probably need to change to the StrifeClientLinux64-0.0.1.12 directory and see what's inside there - hopefully some instructions like a README or INSTALL file that will tell you how to proceed

```

cd StrifeClientLinux64-0.0.1.12

ls

```

---

### Post by Sef on 2014-03-18
> [COLOR=#000000]Now you probably need to change to the StrifeClientLinux64-0.0.1.12 directory and see what's inside there - hopefully some instructions like a README or INSTALL file that will tell you how to proceed[/COLOR]

That is the problem. I cannot find a read / install me file.

Below is what ls gives:


> sef@sef-laptop:~/Downloads/StrifeClient$ ls
base  ca-bundle.crt  icon.png       license.txt      strife.version  updater
bin   game           libraries.txt  strife.manifest  tos.txt


---

### Post by steeldriver on 2014-03-18
There appear to be some instructions in this recent reddit discussion

[http://www.reddit.com/r/linux_gaming/comments/1yh0vx/strife_closed_beta_with_linux_client/](http://www.reddit.com/r/linux_gaming/comments/1yh0vx/strife_closed_beta_with_linux_client/)

In particular

> 
go to the ~/StrifeClient/bin
  start either strife or updater


---

### Post by vasa1 on 2014-03-18
> **Sef said:**
> ...
bash: cd: /home/sef/StrifeClientLinux64-0.0.1.12: No such file or directory
...
I got such an error when I was trying to install  32-bit (unknowingly) Seamonkey on my 64-bit 13.10.

---

### Post by Sef on 2014-03-19
steeldriver:> [COLOR=#000000]There appear to be some instructions in this recent reddit discussion[/COLOR]

[http://www.reddit.com/r/linux_gaming..._linux_client/]("http://www.reddit.com/r/linux_gaming/comments/1yh0vx/strife_closed_beta_with_linux_client/")

[COLOR=#000000]In particular[/COLOR]

[COLOR=#000000][I]go to the ~/StrifeClient/bin

[/I]
[/COLOR]
[COLOR=#000000]*start either strife or updater*[/COLOR]

vasa1:> [COLOR=#000000]I got such an error when I was trying to install 32-bit (unknowingly) Seamonkey on my 64-bit 13.10.[/COLOR]


Thanks for the tips both of you.  I am on vacation for a few days, so I will likely get to this next week.

---

