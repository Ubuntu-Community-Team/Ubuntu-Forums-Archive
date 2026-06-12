---
title: "Gallery Remote -&gt; how to install?"
date: 2007-01-04
forum: General Help
---

### Post by shane2peru on 2007-01-04
I use Gallery on my web page, it is an open source web album.  It comes with my web hosting company.  It has another program that goes with it called Gallery Remote, it allows you to setup your new album on your computer and then just upload it to the Server.  I have used it on windows, and it works nicely.  However I can't get it installed on Ubuntu.  There is a Linux version, and it is a Java type program.  I downloaded the large file (with Java support I think) and the small one, and can't seem to get either to work. [ Here is the Download page.]("http://gallery.menalto.com/wiki/Gallery_Remote")  When I run the shell script here is the output:
```
shane@shane-laptop:~/Downloads$ ./GalleryRemote.1.5.Linux.VM.bin 
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
nawk: error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
hostname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

Launching installer...

grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/tmp/install.dir.16256/Linux/resource/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory

```  I tried to run it with root and get the same errors.  I tried searching for libc.so, but I really don't know how to find them.  Any ideas would greatly be appreciated.  Thanks.

Shane

---

### Post by Jussi Kukkonen on 2007-01-04
Not an answer to you question, but have you thought about using F-Spot? It can export to Gallery without any plugins...

---

### Post by shane2peru on 2007-01-04
I did see that, and did open up F-Spot, however I haven't seen any way that it exports.  I probably just overlooked it. I would be more than willing to give that a try.  Can you point me in the right direction?  Thanks.

Shane

---

### Post by Jussi Kukkonen on 2007-01-04
Should be "Export to Web" or something...

---

### Post by shane2peru on 2007-01-04
Hey there it is.  I guess I would have found it if I had played around with it a little more.  I will have to figure out how to use F-Spot, that is a very nice feature though.  I think I will use it only for my web albums and let it manage them.  I don't like to mess around with naming all my photos.  It will be nice to just export directly to my web album though!  Thanks.  

Shane

---

### Post by rsay on 2007-01-07
I'm having the same problem with gallery remote install. 

I have confirmed that I have all of these libraries. They are located in /lib

libc.so.6
libm.so.6
librt.so.1
libpthread.so.0


Any ideas why this is failing?

p.s. I tried fspot and the upload didn't work for my gallery 2.1. I could see my gallery and albums but got a (500) server error and no picture upload.

---

### Post by rsay on 2007-01-07
Well, 

I've made some progress on this. On another thread I found a reference to a discussion of this problem on the gallery website.

[http://gallery.menalto.com/node/50926]("http://gallery.menalto.com/node/50926") which suggested the following:

Back up the .bin file to name.bin.bak

1. ) cat name.bin.bak | sed "s/export LD_ASSUME_KERNEL/#xport LD_ASSUME_KERNEL/" > name.bin

run the install file

I followed those instructions with the GalleryRemote.Linux.1.5.VM.bin

When I was done I clicked on the link created by the installer and the program failed to run. As I was going to delete the installation directory I happened to run:

```
java -jar GalleryRemote.jar
``` as root and the program ran without a hitch. Now all I have to do is figure out how to make it user executable.

---

### Post by shane2peru on 2007-01-15
rsay,

    Thanks!!!  That worked for me.  I can run it as user.  After the cat line I chmod 777 name.bin file so it could be run as user.  I also installed it in my /home directory.  I don't know if you did it that way, but none the less. Now it tells me there is a new version when I run it.  Thanks for the help.

Shane

Hey I also got fspot to work fine too.  I actually like the interface of F-Spot better.

---

### Post by redhed on 2007-01-21
What did you do to get F-Spot to work?

---

### Post by shane2peru on 2007-01-23
well it isn't flawless.  It keeps messing up sub-ablums, however.  For F-Spot, Select your photos you want to export.  Then click on **File -> Export -> Web Gallery**.  Next we are going to setup the Gallery, click on add, under the Name, it doesn't matter what you put it is the name for you to recognize it as.  The url, will be the location of where **Gallery** is installed ex. [http://www.yourdomainname.com/gallerylocation/](http://www.yourdomainname.com/gallerylocation/)   This is probably the most important part, and difficult part.  Next, your username and password, for your Gallery photo albums.  Next you should be able to click ok, and then click on the albums.  If you want to make a sub-album, or create a new one, or add the pictures to an existing album.  If you did this correctly and already have albums, when you click on the the **Export to Ablum:**  You should see your existing Albums.  If you don't then your settings that we went over above are not correct and you need to double check them.  Then just upload the photos.  It works for me, however if I try and create a sub-album it always puts it in one album, despite what I choose.  I just log in afterwards and move it to where I want it via my web browser.  I hope this helps.  

Shane

---

### Post by Hoshimaru on 2007-02-24
I'm trying to upload pictures to Gallery 2 using F-Spot 0.2.1, but it doesn't work T_T
Here's what I get in the console:
```
Starting upload
uploading 0
open uri = file:///media/Data/Japan/10-17-2005-Tokyo/STA60007.JPG
read = 12806
approximate quality = 97
no options
value = 2007:02:24 13:48:26 len = 19
value = f-spot version 0.2.1 len = 20
Saved 12229 bytes

(f-spot:12443): libf-WARNING **: adding marker: 225, Exif
StatusText : Upload failed\: ''.
Unparsed Line in ParseBasic(): status_debug=1
Upload failed\: ''.
GalleryRemote.GalleryCommandException: Upload failed\: ''.
  at GalleryRemote.Gallery.ParseBasic (System.Net.HttpWebResponse response) [0x00000] 
  at GalleryRemote.Gallery.ParseAddItem (System.Net.HttpWebResponse response) [0x00000] 
  at GalleryRemote.Gallery2.AddItem (GalleryRemote.Album album, System.String path, System.String filename, System.String caption, Boolean autorotate) [0x00000] 
  at GalleryRemote.Album.Add (.Photo photo, System.String path) [0x00000] 
  at FSpot.GalleryExport.Upload () [0x00000] 

```
Any ideas? My host doesn't support it ? ([www.free.fr](www.free.fr))

---

### Post by shane2peru on 2007-02-24
I don't know that I can be of much help.  I don't make much of the error output.  I would 

1.  Check all your server settings in F-Spot and make sure they are setup correctly.  I had to do it once or twice just to figure it out.  The most critical thing is the album location.  If that isn't right, it is not going to login.  Your url should be something like this:  [www.yourdomainname.com/youralbumfoldername](www.yourdomainname.com/youralbumfoldername)  So when you copy and paste that into your browser it brings up your photo album.  

2. Also I have found that if I go in and manually make my Album online then just upload the files to that empty album it works much better.  If I try and make an album with F-Spot it never puts it in the right spot, and I end up with it as a sub-album of some other album where it doesn't belong.

Shane

---

### Post by Hoshimaru on 2007-02-24
I found out the pics got uploaded in the right directory, but they don't appear in the Album itself. Very strange.

Update: pics don't always get uploaded correctly. My Gallery settings seem to be correct.
Settings: [http://img398.imageshack.us/img398/3927/screenshotxe9.png](http://img398.imageshack.us/img398/3927/screenshotxe9.png)

Error: [http://img526.imageshack.us/img526/5552/screenshot1ep8.png](http://img526.imageshack.us/img526/5552/screenshot1ep8.png)

---

### Post by Nubbie on 2007-04-24
I agree 100%, F-Spot is great!
I never knew it could sync up to Gallery. I thought it just built web pages with the pictures in them.
All are advised to at least TRY f-spot out before trying to mess around with this Gallery Remote business.

---

### Post by ThomasNovin on 2007-05-25
> **rsay said:**
> Well, 

run the install file

I followed those instructions with the GalleryRemote.Linux.1.5.VM.bin

When I was done I clicked on the link created by the installer and the program failed to run. As I was going to delete the installation directory I happened to run:

```
java -jar GalleryRemote.jar
``` as root and the program ran without a hitch. Now all I have to do is figure out how to make it user executable.

On the step on which Java Virtual Machine to use, I pointed to ```
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/bin
```. 

After the install I went into my install-directory ran the Gallery_Remote shellscript through the same sed-command as I was supposed to do with the installer.

```

$ mv Gallery_Remote Gallery_Remote.bak
$ cat Gallery_Remote.bak | sed "s/export LD_ASSUME_KERNEL/#xport LD_ASSUME_KERNEL/" > Gallery_Remote 
$ chmod +x Gallery_Remote
```

Running as a user is not a problem!

Ps. I have done the install as a user as well, into my own home directory.

---

### Post by James Wilford on 2007-08-01
ThomasNovin, I followed your instructions and managed to get it to start up. However, I now just get a blank grey window - the Gallery Remote interface does not appear.

There is no sign of cpu activity and I have left it for a while but nothing appears. Any help would be appreciated.

---

### Post by DannyW on 2007-09-15
> **ThomasNovin said:**
> On the step on which Java Virtual Machine to use, I pointed to ```
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/bin
```. 

After the install I went into my install-directory ran the Gallery_Remote shellscript through the same sed-command as I was supposed to do with the installer.

```

$ mv Gallery_Remote Gallery_Remote.bak
$ cat Gallery_Remote.bak | sed "s/export LD_ASSUME_KERNEL/#xport LD_ASSUME_KERNEL/" > Gallery_Remote 
$ chmod +x Gallery_Remote
```

Running as a user is not a problem!

Ps. I have done the install as a user as well, into my own home directory.

Thanks, worked a charm.

---

### Post by Hoppiesbox on 2007-10-05
Just reading here and - I've really got to agree with the others who recommend f-spot. Here are the steps

1. create a new tag. name it todays date or whatever
2. select the photos you want to add
3. right click on the tag you created and select 'Attach tag to selection'

You can skip steps 1 and 3 if you are only doing a small number - but if you select 100 photos and something happens to deselect them....you're going to wish you had tagged them. Hopefully soon f-spot will have a 'tray' like picasa uses...

4. go File>Export>Export to Web Gallery
5. add your online Gallery if its the first time - don't forget http:// in the address :)
6. select the album you'll be uploading to 
7. set your other options
8. start the upload
9. get a cup of coffee

Hope this helps anyone who's confused

---

### Post by ferrocene on 2008-06-30
As a FYI, F-Spot will not connect to a Gallery2 install that is on a SSL-enabled website (https, 443).  I get an error.  :(

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=375387](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=375387)

[http://bugzilla.gnome.org/show_bug.cgi?id=473417](http://bugzilla.gnome.org/show_bug.cgi?id=473417)

---

