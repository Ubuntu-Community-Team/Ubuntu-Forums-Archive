---
title: "Can't uninstall Xeoma"
date: 2012-11-18
forum: General Help
---

### Post by Fuji_in_Japan on 2012-11-18
hello,

I installed Xeoma through the Ubuntu Software center and now cannot uninstall.  I still have XeomaCore and XeomaClient loading at start up.

-  Unistalled through the software center.  However it didn't uninstall although the center says it did.

-  tried sudo apt-get remove Xeoma (along with all variants client and core) and still can't remove the software.

Any suggestions?

On a separate note, how do I get to rate this software in the software center?

Best regards,
Dave

---

### Post by NikTh on 2012-11-18
> **Fuji_in_Japan said:**
> hello,

I installed Xeoma through the Ubuntu Software center and now cannot uninstall.  I still have XeomaCore and XeomaClient loading at start up.

-  Unistalled through the software center.  However it didn't uninstall although the center says it did.

-  tried sudo apt-get remove Xeoma (along with all variants client and core) and still can't remove the software.

Any suggestions?

Hi , 
Open a terminal and use this command 
```
sudo apt-get purge $(dpkg -l | awk '/^rc/ { print $2 }')
```Post the results back here if you want. 
Click on "New Reply" and put the results inside [CODE] tags to be easier to read. [See here how]("http://i.stack.imgur.com/zADbK.png")

> **Fuji_in_Japan said:**
> On a separate note, how do I get to rate this software in the software center?
First of all you have to install the software (as you did) , then you should have a Software Center account. If you don't , just create one. SSO is a requirement. 
For more , read here =>[RatingsAndReviews]("https://wiki.ubuntu.com/SoftwareCenter/RatingsAndReviews")
Thanks

---

### Post by Fuji_in_Japan on 2012-11-18
Hello,

I tried your advice but unfortunately it didn't work.  

Code is below.

                          ```
Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 The following packages were automatically installed and are no longer required:  
   gimp-help-en gimp-help-common  
 Use 'apt-get autoremove' to remove them.  
 The following packages will be REMOVED: 
   gimp* gimp-data* libavcodec53* libavutil51* libbabl-0.0-0* libblas3gf* libgegl-0.0-0* libgfortran3* libgimp2.0* libgtkglext1*  
   libgutenprintui2-1* liblapack3gf*  
 0 upgraded, 0 newly installed, 12 to remove and 0 not upgraded.  
 After this operation, 0 B of additional disk space will be used.  
 Do you want to continue [Y/n]? Y  
 (Reading database ... 325286 files and directories currently installed.)  
 Removing gimp ...  
 Purging configuration files for gimp ...  
 Removing gimp-data ...  
 Purging configuration files for gimp-data ...  
 Removing libavcodec53 ...  
 Purging configuration files for libavcodec53 ...  
 Removing libavutil51 ...  
 Purging configuration files for libavutil51 ...  
 Removing libbabl-0.0-0 ...  
 Purging configuration files for libbabl-0.0-0 ...  
 Removing libblas3gf ...  
 Purging configuration files for libblas3gf ...  
 Removing libgegl-0.0-0 ...  
 Purging configuration files for libgegl-0.0-0 ...  
 Removing libgfortran3 ...  
 Purging configuration files for libgfortran3 ...  
 Removing libgimp2.0 ...  
 Purging configuration files for libgimp2.0 ...  
 Removing libgtkglext1 ...  
 Purging configuration files for libgtkglext1 ...  
 Removing libgutenprintui2-1 ...  
 Purging configuration files for libgutenprintui2-1 ...  
 Removing liblapack3gf ...  
 Purging configuration files for liblapack3gf ...  

```Any other advice is most appreciated.

See screenshot here:
[[IMG]http://img15.imageshack.us/img15/9113/xeomascreenshot.jpg[/IMG]](http://imageshack.us/photo/my-images/15/xeomascreenshot.jpg/)

Uploaded with [ImageShack.us](http://imageshack.us)

Dave

---

### Post by NikTh on 2012-11-18
This is weird really. You know , I searched for this program through apt-get and I cannot find anything. ```
apt-cache search xeoma
``` , I used synaptic package manager but to no avail , maybe another name ? 

**[offtopic]**I don't know why such programs approved for Ubuntu software center , but this is just my opinion. As I read in [reviews]("https://apps.ubuntu.com/cat/applications/precise/xeoma/reviews/") (because I haven't tested it) is a commercial program with lot of restrictions and this is not mentioned in description. (also a restricted and not open source program). **[/offtopic]**

Try to locate the program with locate command ```
locate <program name>
``` and use rm command (carefully) to delete any remains.

Also take a look in software center (history or installed) and try to locate what installed through this program. 

Also you can take a look in dpkg-log and see if something is there (about what program(s) installed through this xeoma)
```
cat /var/log/dpkg.log > dpkg.txt
gedit dpkg.txt
```Thanks

---

### Post by Fuji_in_Japan on 2012-11-18
Hello,

Here is what I am getting:

```
apt-cache search xeoma
xeoma - Construction-set principle video surveillance software
xeoma-bin - Construction-set principle video surveillance software

```Locate xeoma didn't find anything:

```
dave@Ubuntu-VirtualBox:~$ locate xeoma
dave@Ubuntu-VirtualBox:~$ sudo locate xeoma
dave@Ubuntu-VirtualBox:~$ 
```Nor did Locate xeoma-bin

What's most interesting is the history in the software center says it was removed?  But it tries to load everytime I boot 
[[IMG]http://img32.imageshack.us/img32/2203/xeomaremoved.jpg[/IMG]]("http://imageshack.us/photo/my-images/32/xeomaremoved.jpg/")

Uploaded with [ImageShack.us]("http://imageshack.us")

Additional information: Found the program under /home/dave/bin/Xeoma and I renamed the program.  Well see what that does?

dave

---

### Post by NikTh on 2012-11-19
Hi , 
good thought. Search in bin and/or sbin and try to locate any remains. Rename them and see if better. If yes , I think you can remove them safely , with rm command. 
Also you can use find command like this
```
sudo find / -iname xeoma
```Thanks

---

