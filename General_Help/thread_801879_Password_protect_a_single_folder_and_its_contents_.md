---
title: "Password protect a single folder and its contents w/o encryption"
date: 2008-05-21
forum: General Help
---

### Post by theytookpenny on 2008-05-21
What I want to do seems very simple to me, except I have no idea how to do it. I would like to password protect a folder and all of the contents within it. To be very specific, I would like a method that would allow me to, upon clicking the folder, enter a password into a window. Mind that I do NOT want to encrypt it, as it seems that encrypting does not protect the actual folder but instead creates a zip, I would like the folder to remain as it is: a folder. Once accessed, the contents of the folder should be able to be written, deleted or edited as if they were regular files elsewhere. Also, I want it so that I must enter a password EVERY time I try to access the folder. I do NOT want it so that all the documents have to be accessed through the password, just the parent folder. Is there a way to do this?

---

### Post by Wim Sturkenboom on 2008-05-21
This is not an answer to the question, but why would you want to do that?

Linux is a multiuser system, so you can setup multiple users. You can also set permissions so other users can not see the folder and hence can not access it.

---

### Post by theytookpenny on 2008-05-21
Yes, I already know about these options and I'd prefer not to do them. I know I can chmod the folder, but I don't want to have to use the terminal to access it, also, creating users would be too much of a hassle, since the laptop is used almost always only by me. On the few occasions that others do use it, I simply just want that directory to be inaccessible to them.

---

### Post by cdtech on 2008-05-21
Permissions the only way. Put the folder on a USB drive.

---

### Post by bodhi.zazen on 2008-05-21
Currently you have only 2 options :

encryption and permissions.

Since you do not want to use permissions ... I suggest you look at truecrypt. truecrypt is very easy to install and use and has a gui.

Getting back to permissions : Make a directory in say /root that is owned only by root (permissions 700). Then to access the files, use 

```
(nohup gksu nautilus --no-desktop)
```

Last question, why so adverse to the command line ? Once you learn your way around the command line is very easy and helpful. The attitude of avoiding the command line at all costs sometimes makes life harder then it has to be.

---

### Post by digitalvectorz on 2008-05-21
> 
Mind that I do NOT want to encrypt it, as it seems that encrypting does not protect the actual folder but instead creates a zip


encrypting (alone) shouldn't create a zip...that's compression.

---

### Post by bodhi.zazen on 2008-05-21
You can use zip to archive the directory and password protect the archive

zip -p password dir

BUT : > 
**-P** *password*
              use *password* to encrypt zipfile entries (if any).  **THIS** **IS** **INSE-**
              **CURE!**  Many multi-user operating systems provide  ways  for  any
              user  to see the current command line of any other user; even on
              stand-alone systems there is  always  the  threat  of  over-the-
              shoulder  peeking.   Storing the plaintext password as part of a
              command line in an automated script  is  even  worse.   Whenever
              possible, use the non-echoing, interactive prompt to enter pass-
              words.  (And where  security  is  truly  important,  use  strong
              encryption such as Pretty Good Privacy instead of the relatively
              weak encryption provided by standard zipfile utilities.

---

### Post by theytookpenny on 2008-05-21
> Last question, why so adverse to the command line ? Once you learn your way around the command line is very easy and helpful. The attitude of avoiding the command line at all costs sometimes makes life harder then it has to be.

It's not that I don't want to use the command line, its just that for this occasion, I would hate to have to open the terminal to access the files that I frequently use.

> encrypting (alone) shouldn't create a zip...that's compression.

Either way, when I try to encrypt the folder, it creates a pgp that may be decrypted, but leaves the actual folder there, unprotected and unaltered. I want that folder to be (password) protected, but encrypting only makes another version of it in zip format.

> 
You can use zip to archive the directory and password protect the archive

Like I said, I do not want to actually zip the folder, I just want to protect it so that all I need to do to access/edit/remove/etc is enter a password. Zipping it won't let me do all that (at least not without taking an unreasonably longer time).

---

### Post by bodhi.zazen on 2008-05-21
We understand what you want, but this feature is not available. You will have to choose the best work around.

My advice stands, make a folder owned by root with permissions of 700

access with gksu nautilus --no-desktop

Make a launcher if you want, on your menu, with the command :

gksu nautilus --no-desktop /path/to/dir

About as good as it is going to get for you.

---

### Post by ryanhaigh on 2008-05-22
No idea if this would work as Im on windows at the moment and cant test it but what about using something like the script below?

```

#!/bin/bash

#run a 'dummy' sudo command to get a password prompt, if the command #doesn't succeed then the && should stop the rest of the script from #running, if thats not the case then you could put in something to check #for the file or some other check
gksudo touch /tmp/tempfile && 

#change persmissions to allow access
chmod +rwx /path/to/folder -R &&

#open nautilus and wait till its finished before moving on
#im assuming that this will spawn another instance of nautilus and that when you close the window it will continue
nautilus /path/to/dir &&

#change the permissions again
chmod -rwx /path/to/dir -R
exit

```

If this does actually work, and I won't be suprised if it doesn't as I have made a couple of assumptions I cannot test at the moment, then you can create a launcher which will call the script so you don't have to use the command line.

---

### Post by Keith Hedger on 2008-05-24
This may be along the lines you want:
Make a file in ~/.gnome2/nautilus-scripts called LockFolder
and add these lines to it```
#!/bin/bash
foo=$(gksudo -u root -k -m "Enter Your Admin Password" /bin/echo "got r00t?")
sudo chmod 0 $1
```

make the script executable then make another file in ~/.gnome2/nautilus-scripts called UnLockFolder
and add these lines to it:```
#!/bin/bashLockFolder
foo=$(gksudo -u root -k -m "Enter Your Admin Password" /bin/echo "got r00t?")
sudo chmod 755 $1
```
make the script executable

To use just right click on the folder and select LockFolder/UnLockFolder from the scripts menu to lock/unlock the folder.
Not a perfect solution but is probably the nearest to what you want.

---

### Post by chrisccoulson on 2008-05-24
I can't see how something like [Cryptkeeper]("http://www.tomatarium.pwp.blueyonder.co.uk/cryptkeeper.html") doesn't do what you want

---

### Post by theytookpenny on 2008-05-25
So far the ideas I like most are the script and the lock/unlock in nautilus.

```
#!/bin/bash

#run a 'dummy' sudo command to get a password prompt, if the command #doesn't succeed then the && should stop the rest of the script from #running, if thats not the case then you could put in something to check #for the file or some other check
gksudo touch /tmp/tempfile && 

#change persmissions to allow access
sudo chmod -c 777 /home/penny/.Restricted -R &&

#open nautilus and wait till its finished before moving on
#im assuming that this will spawn another instance of nautilus and that when you close the window it will continue
nautilus /home/penny/.Restricted &&

#change the permissions again
sudo chmod -c 000 /home/penny/.Restricted -R
exit
```

I changed the script only slightly, making it -c xxx instead of -rwx and added sudo as the folders that I created where made with root. The only problem is that when I run it, the script goes through the whole code before I even get to access the files. How can I get it to pause at "nautilus /home/penny/.Restricted &&" before it goes on to the next code?


As for the lock and unlock scripts, lock works, I can lock all the folders I want, but unlock does not. When I click on unlock, it just leaves the folders with their same locked permissions

---

### Post by ryanhaigh on 2008-05-25
As I said I assumed that calling nautilus would spawn another instance which when terminated would allow the script to continue. It seems that this assumption was incorrect and you will have to use another method to determine when the nautilus window is closed. For example you could use something like:
```

#start nautilus in the background
nautilus /path --no-desktop &
#get the pid of the launched nautilus process
nautiluspid = $!
#test whether that process is still running by sending a singal 0 to the 
#process
kill -s 0 $nautiluspid
#while the exit status of the test is 0 the process is still running
#wait till the process can't recieve the 0 signal and is therefore no 
#longer running
while [ $? == 0 ]
do
  #wait 1 second
  sleep 1s
  #check again
  kill -s 0 $nautiluspid
done
#continue if the process no longer exists

```


Once again I am not on a Linux machine at the moment so I can't test this but it should at least give you a starting point.

If these files are owned by root then I don't think its necessary to have this level of complexity. Simply keep the files as owned by root with only root having rwx privileges, install [apt://nautilus-gksu](apt://nautilus-gksu) and then you will get a right click option to open as administrator, which will prompt you for your admin password and open a new nautilus window. Be aware that this instance of nautilus is running with root privileges so be careful, this is probably the only advantage to using the scripts that have been provided here.

---

### Post by theytookpenny on 2008-05-26
That bit of code you just gave me, Ryan, is a little too complex for me to understand. Should I add this code right before "chmod -c 0"?

And...
> **ryanhaigh said:**
> 
If these files are owned by root then I don't think its necessary to have this level of complexity. Simply keep the files as owned by root with only root having rwx privileges, install [apt://nautilus-gksu](apt://nautilus-gksu) and then you will get a right click option to open as administrator, which will prompt you for your admin password and open a new nautilus window. Be aware that this instance of nautilus is running with root privileges so be careful, this is probably the only advantage to using the scripts that have been provided here.

I don't want to risk accidentally risk accessing a root folder/file and altering the data. I even thought of that option when I edited the script (I did a LOT of editing before I decided to leave it as it is). Unfortunately, because it adds the administrator privleges to the user on all folders/files accessed, I don't want to risk it. I know it may sound a little over the top, but this is just something I have to be self-assured about.

---

### Post by ryanhaigh on 2008-05-26
```

#!/bin/bash

#run a 'dummy' sudo command to get a password prompt, if the command #doesn't succeed then the && should stop the rest of the script from #running, if thats not the case then you could put in something to check #for the file or some other check
gksudo touch /tmp/tempfile && 

#change persmissions to allow access
sudo chmod -c 777 /home/penny/.Restricted -R &&

#open nautilus and wait till its finished before moving on
#start nautilus in the background
nautilus /home/penny/.Restricted &

#get the pid of the launched nautilus process
#$! is a special variable that always contains the pid of the last process started in background
nautiluspid = $!

#test whether that process is still running by sending a singal 0 to the 
#process, see man signal or man kill for more info
kill -s 0 $nautiluspid

#while the exit status of the test is 0 the process is still running
#wait till the process can't recieve the 0 signal and is therefore no 
#longer running
#$? is a special variable containing the exit status of the last run program (in our case the kill command)
while [ $? == 0 ]
do
  #wait 1 second
  sleep 1s
  #check again
  kill -s 0 $nautiluspid
done
#if we get here the process no longer exists, continue

#change the permissions again
sudo chmod -c 000 /home/penny/.Restricted -R
exit

```

Not wanting to run nautilus as root is perfectly reasonable, you could just change the ownership so that you don't have to use sudo in the script.

This is a great resource if you want to do some bash scripting: [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/) you don't need to do/read everything to get started you can just learn as the task requires.

---

### Post by asdir on 2008-09-23
@cryptkeeper: Did I understand that right? It allows me to encrypt a folder that, even if copied to somewhere else (say through Dropbox), would still stay encrypted and could only be read with my setting, i.e. on my PC?

---

### Post by madcreation on 2008-11-11
wow thanks a lot crypt keeper works, was wondering how i could do that!

---

### Post by bodhi.zazen on 2008-11-11
This is an old thread. Encryption is now available (as of 8.10)

[https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

---

