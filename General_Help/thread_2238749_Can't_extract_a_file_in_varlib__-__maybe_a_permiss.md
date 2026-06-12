---
title: "Can't extract a file in /var/lib/  -  maybe a permission problem"
date: 2014-08-09
forum: General Help
---

### Post by walterdowis on 2014-08-09
Hi All,
 
    I'm trying to extract an archive file in /var/lib/boinc-client.  I've used two methods to do the extract:
    
    1. In command line I type in ```
sudo su
cd /var/lib/boinc-client
tar xfz setiathomev7-armv6l.tar.gz
```  I get an error message "no such file or directory".  (I know the file is in this directory because I see it with the ls command).

 2. With file manager I go into /var/lib/bonic-client and I see the file.  I double click on the file and archive manager comes up with the file.         I click on the extract button but I get this error message:  "you don't have the right permissions to extract archives in the folder"

 It seems I may a permission problem.  I'm running Ubuntu on a HummingBoard which is somewhat similar to a Raspberry Pi.  I am a little new to command line and have a beginner's level experience with it.  Is there a way to extract this file?  

  Thanks.

---

### Post by steeldriver on 2014-08-09
The 'f' (filename) option of tar expects to be followed immediately by the filename so 'tar xfz whatever' is looking for a file called 'z' - you need to change the order to 'xzf'

In fact, I'd omit the 'z' since modern versions of tar can infer the compression format - I'd also suggest using plain sudo instead of 'sudo su'

```
cd [COLOR=#444444][FONT=Arial]/var/lib/boinc-client
sudo tar xf [FONT=Arial][COLOR=#444444]setiathomev7-armv6l.tar.gz[/COLOR][/FONT][/FONT][/COLOR]
```[COLOR=#444444][FONT=Arial]

(actually I usually use 'tar x**v**f' cos it's just nice to see what the archive contains). FYI tar also has a -C option which means you don't need to place the archive file in the target directory e.g. you can have it in your regular ~/Downloads directory and then do something like

```
sudo tar xvf ~/Downloads/somefile.tar.gz -C /var/lib/somedir/
```
[/FONT][/COLOR]

---

