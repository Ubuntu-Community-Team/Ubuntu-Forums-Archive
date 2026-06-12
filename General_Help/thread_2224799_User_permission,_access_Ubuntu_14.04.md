---
title: "User permission, access Ubuntu 14.04"
date: 2014-05-18
forum: General Help
---

### Post by kemoc-forum on 2014-05-18
I found problem/bug (i think). 
I updated Ubuntu 13.10 -> 14.04 by popup window in ubuntu.
I added my user e.g.: radek to another user group, that group has permission to write in some directory/files but not my user.
Added my user to other group do not merge permissions!
I cannot add/edit files only I can read as was before.

I have Ubuntu 12.04 on other PC and there is correct. I added user to some group and I got that group permissions.

look at the image, please.
[http://imgur.com/djFjHBL](http://imgur.com/djFjHBL)

---

### Post by christo3 on 2014-05-18
I'm not sure I fully understand your problem. I had a problem where I removed my only admin account from the adm and sudo user groups.
I used the usermod command-line function. Very dangerous if you not fimiliar with it.
There is a possible solution on askUbuntu [http://askubuntu.com/questions/29004/regain-sudo-rights-after-removing-from-admin-group](http://askubuntu.com/questions/29004/regain-sudo-rights-after-removing-from-admin-group)
I suggest using a live-cd or live-usb and saving files to external drive then do a fresh install. If you comfortable with the command-line 
This is what I did:
1. get a new live-cd or live-usb
2. boot to it
3. open a terminal
4. mount your filesystem drive
5. go to /etc/
6. edit group with nano
7. add your user to adm and sudo like so : goto the line containing adm and sudo respectively add a colon followed by username
Hope this helps

---

### Post by kemoc-forum on 2014-05-18
Probably i have to do fresh install, but my user (radek) is in adm and sudo and root group, did you (@[**[COLOR=#000000]christo3[/COLOR]**]("http://ubuntuforums.org/member.php?u=1918602")) see the image?
Result of command: 'groups radek' is on bottom.

You did not understand me.

But one more thing, user radek has permissions from root group, radek permissions are extended by root group permissions but not by wwwdatad, www-data geoups.

---

### Post by christo3 on 2014-05-19
Sorry my ISP blocked the URL for the image.
I think I understand your question relates to file permissions for the directory.
Have you tried setting file permissions using  "sudo chmod -R 775 directory" in terminal.
This grants owners and group read,write,execute access and everybody else read and execute access.

---

### Post by kemoc-forum on 2014-05-19
I have to said again you did not. So if you cannot open this url use some proxy. You have really strange ISP :P
it is really important to see this image.

---

### Post by christo3 on 2014-05-20
Maybe post the image on flickr. I can acess flickr.

---

### Post by Impavidus on 2014-05-20
Instead of fussing with screenshots, try getting the same info in the terminal and just post it here [noparse]```
between code tags
```[/noparse]:```
ls -l htdocs
ls -l htdocs/UntitledFolder
groups radek
#And concluding you cannot write to "htdocs/UntitledFolder/Untitled Document (Copy)"
```That makes it easy to read for all of us. Terminal output is usually the preferred way. Else attach the screenshot to a post in the forum (as an attachment).

The directory you try to write to belongs to the group wwwdatad, to which you also belong, and has write permission for the group. This should give you the right to create and delete files in that directory. The file belongs to the group radek, to which you also belong, and has write permission for the group. This should give you the right to modify this file. This fails. Unfortunately the error message is not very clear concerning the reason why it fails.

Maybe writing to that file using the terminal gives a clearer error message. Try```
echo test >"htdocs/UntitledFolder/Untitled Document (Copy)"
```

On a sidenote: I'm not sure it's a good idea to be part of the group root. By default you are not. Having all those files in your home directory owned by user wwwdatad is quite messy and may lead to trouble.

---

### Post by kemoc-forum on 2014-05-22
> **Impavidus said:**
> Instead of fussing with screenshots, try getting the same info in the terminal and just post it here [noparse]```
between code tags
```[/noparse]:```
ls -l htdocs
ls -l htdocs/UntitledFolder
groups radek
#And concluding you cannot write to "htdocs/UntitledFolder/Untitled Document (Copy)"
```That makes it easy to read for all of us. Terminal output is usually the preferred way. Else attach the screenshot to a post in the forum (as an attachment).
...


Thanks,
ok I try to write again:
```
radek@radek:~$ ls -l
drwxrwxrwx+  8 radek radek   4096 May 18 16:07 htdocs
radek@radek:~$ 

```

```
radek@radek:~/htdocs/UntitledFolder$ ls -l
-rw-rw-r--+ 1 radek    radek       0 May 18 11:31 Untitled Document
-rw-rw-rw-+ 1 wwwdatad wwwdatad    0 May 18 11:34 Untitled Document3
-rw-rw-r--+ 1 wwwdatad radek       0 May 18 11:31 Untitled Document (copy)
drwxrwxr-x+ 2 radek    radek    4096 May 18 11:31 UntitledFolder
drwxrwxr-x+ 2 wwwdatad wwwdatad 4096 May 18 11:35 UntitledFolder2
drwxrwxr-x+ 2 wwwdatad radek    4096 May 18 11:35 UntitledFolder3

```

```
radek@radek:~/htdocs/UntitledFolder$ groups radek 
radek : radek root adm cdrom sudo dip www-data plugdev lpadmin sambashare wwwdatad

```


> **Impavidus said:**
> ...
Maybe writing to that file using the terminal gives a clearer error  message. Try```
echo test >"htdocs/UntitledFolder/Untitled Document  (Copy)"
```


Result:
```
radek@radek:~/htdocs/UntitledFolder$ echo test > Untitled\ Document\ \(copy\) 
bash: Untitled Document (copy): Permission denied
radek@radek:~/htdocs/UntitledFolder$ 

```

> **Impavidus said:**
> 
On a sidenote: I'm not sure it's a good idea to be part of the group  root. By default you are not. 

I know that but almost all root user files for group root has that same permissions as for Other.
For me belogs to root group is comfortably.

> **Impavidus said:**
> Having all those files in your home  directory owned by user wwwdatad is quite messy and may lead to  trouble. 
If it cause some trobbles for operating system then that system should be thrown to rubbish bin.
PS.: I created this folder, it did not do by OS.

Thanks for help.

---

### Post by Impavidus on 2014-05-22
The plus sign at the end of the permissions indicates that these files and directories use access control lists, an extension to the POSIX permissions usually used. So even though your group has write permission, you don't. I don't know about ACLs, but undoubtedly there are some tutorials around on the net. This also explains the lock on your UntitledFolder, as shown in your screenshot.

The OS itself has no problem with the wwdatad-owned files in your home directory, but it prevents you from managing all files in your home directory without using sudo. Even with write access, you cannot chmod files when you're not the owner.

---

### Post by kemoc-forum on 2014-05-22
Thanks a lot, i will check ACL. 
Super user (sudo - super user do) also is needed to change file owner I know that, I know Linux/Ubuntu a little bit.

You are 100% right.
```
radek@radek:~/htdocs$ getfacl UntitledFolder
# file: UntitledFolder
# owner: wwwdatad
# group: wwwdatad
user::rwx
user:www-data:rwx
group::r-x
mask::rwx
other::rwx
default:user::rwx
default:user:www-data:rwx
default:group::r-x
default:mask::rwx
default:other::r-x


```

---

### Post by kemoc-forum on 2014-05-22
Solution for community:
1. in terminal you heve to be in parent or upper
2. template "scope::rule" like is output getfacl
3. usefull page: [http://linux.about.com/library/cmd/blcmdl1_setfacl.htm](http://linux.about.com/library/cmd/blcmdl1_setfacl.htm)

```
radek@radek:~/htdocs$ sudo setfacl -m "group::rwx" UntitledFolder
radek@radek:~/htdocs$ sudo getfacl UntitledFolder
# file: UntitledFolder
# owner: wwwdatad
# group: wwwdatad
user::rwx
user:www-data:rwx
group::rwx
mask::rwx
other::rwx
default:user::rwx
default:user:www-data:rwx
default:group::r-x
default:mask::rwx
default:other::r-x

radek@radek:~/htdocs$ sudo setfacl -m "default:group::rwx" UntitledFolder
radek@radek:~/htdocs$ sudo getfacl UntitledFolder# file: UntitledFolder
# owner: wwwdatad
# group: wwwdatad
user::rwx
user:www-data:rwx
group::rwx
mask::rwx
other::rwx
default:user::rwx
default:user:www-data:rwx
default:group::rwx
default:mask::rwx
default:other::r-x

radek@radek:~/htdocs$ sudo setfacl -R -m "group::rwx" UntitledFolder
radek@radek:~/htdocs$
```

BR

---

