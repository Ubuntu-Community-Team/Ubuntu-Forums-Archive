---
title: "Unable to Instal Software"
date: 2008-04-27
forum: General Help
---

### Post by Utnubuster on 2008-04-27
I'm trying to instal Floola. It runs on ubuntu and debain. See [http://tiny.cc/CVYNY](http://tiny.cc/CVYNY) . So it told me to enter a line in the terminal, which succeded. But I get this 

[http://s93.photobucket.com/albums/l48/J0ey790/?action=view&current=Problem.png](http://s93.photobucket.com/albums/l48/J0ey790/?action=view&current=Problem.png)

Help appreciated. Sorry if this post looks messy or unorganized.

---

### Post by Glaxed on 2008-04-27
What line did you enter in the terminal?

---

### Post by Utnubuster on 2008-04-28
This sudo apt-get install libnotify-bin

it told me to on the site listed above

---

### Post by Glaxed on 2008-04-28
Right, I think that file-roller just isnt unpacking the tar.gz.
Try extracting all of the files and then installing.

---

### Post by Utnubuster on 2008-04-29
> **Glaxed said:**
> Right, I think that file-roller just isnt unpacking the tar.gz.
Try extracting all of the files and then installing.

I tried but I can't get it to work. I tried extracting the the "documents" folder and my desktop. The readme opens but not floola. When I click (also tryed right clicking then clicking "open") nothing happens. Not even saying "starting floola" like it does with other applications. I tried to "open with" also. I tried almost everything to open with but It will not open. It's on my desktop and the icon is a diamond with two gears in it. Is that the instaler logo?

---

### Post by Glaxed on 2008-04-29
Ok, open a terminal and type;
```

$ sudo chmod a+x floola
$ ./floola
# where floola is that complete pathname to the main floola binary

```

---

### Post by Utnubuster on 2008-04-29
Maybe I'm doing it wrong I copied everything and I got this. 

joey@joey-desktop:~$ $ sudo chmod a+x floola
bash: $: command not found
joey@joey-desktop:~$ $ ./floola
bash: $: command not found
joey@joey-desktop:~$ # where floola is that complete pathname to the main floola binary

it can't find floola.

The help is very appreciated, by the way. Thanks:)

---

### Post by Glaxed on 2008-04-29
:D - yes, you are doing two things wrong (though I remember doing this myself.)

When I used $ in my post, it meant for you to run the following command in the terminal, so if someone posts '$ sudo apt-get update' it means;
joey@joey-desktop:~$ sudo apt-get update

Secondly, the floola (or whatever it is called package) is probably not in your home directory. Is it extracted on your desktop?
If so, then type

joey@joey-desktop:~$ cd ~/D*
joey@joey-desktop:~$ sudo chmod a+x flo*
joey@joey-desktop:~$ ./flo*

Note; * is  a wildcard. When you give the shell (terminal, or console - on Ubuntu, BASH is used) a wildcard, it tries to guess what file or directory you are specifying. This is useful if the filename is too long, and there is nothing spelled remotely like it in the same directory.
joey@joey-desktop:~$ cd ~/D*
is the same as
joey@joey-desktop:~$ cd ~/Desktop
is the same as
joey@joey-desktop:~$ cd /home/joey/Desktop

Likewise, I used flo* because I'm guessing there isnt another file starting with the 'flo' on your Desktop.

---

### Post by Utnubuster on 2008-04-30
Oh the $'s meant terminal:). I tried the code but it didn't work. Am I to extract it somewhere else? I typed:

joey@joey-desktop:~$ sudo chmod a+x floola*
chmod: cannot access `floola*': No such file or directory
joey@joey-desktop:~$ sudo chmod a+x floola-linux.tar.gz*
chmod: cannot access `floola-linux.tar.gz*': No such file or directory
joey@joey-desktop:~$ sudo chmod a+x floola-linux.tar.gz
chmod: cannot access `floola-linux.tar.gz': No such file or directory
joey@joey-desktop:~$ 

I also couldn't find a directory to extract it too. The tar.gz file is extracted right on the desktop aswell as documents and and file where it's extracted from  is on my desktop. It's not finding it

---

### Post by jocko on 2008-04-30
I downloaded floola just to see what the problem is, and it seems to run fine for me.
Did you extract the file to your desktop (to a foler called "Floola-linux"?
Then, try this in a terminal:
```
cd ~/Desktop/Floola-linux
./Floola
```
Does it work?
If it doesn't is there any error message?
And what's the point of that program?
I generally don't trust webpages with that extreme amount of ads on them... "Shorten your URL"? What's that about?

---

### Post by blenderfish on 2008-04-30
I am having the same issue.  When I navigate to where I extracted the files to, and I try to execute Floola, nothing happens.  See below:

 ```
me@computer:~/Desktop/Floola-linux$ Floola
bash: Floola: command not found
me@computer:~/Desktop/Floola-linux$ ./Floola 
./Floola: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

```

Any ideas?   Floola is listed as an executable.  I have the libstdc++6 package installed.

---

### Post by Glaxed on 2008-04-30
It may be that the libstdc++6 package you have is outdated or too new for Floola.. You said that you have a Floola binary - have you tried compiling from source?

---

### Post by jocko on 2008-05-01
> **blenderfish said:**
> I am having the same issue.  When I navigate to where I extracted the files to, and I try to execute Floola, nothing happens.  See below:

 ```
me@computer:~/Desktop/Floola-linux$ Floola
bash: Floola: command not found
me@computer:~/Desktop/Floola-linux$ ./Floola 
./Floola: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

```Any ideas?   Floola is listed as an executable.  I have the libstdc++6 package installed.

Try this:
```
[FONT=monospace]sudo ln -s /usr/lib/libstdc++.so.6 /usr/lib/libstdc++.so.5[/FONT]
```

---

### Post by kdjtar on 2009-03-06
> **blenderfish said:**
> I am having the same issue.  When I navigate to where I extracted the files to, and I try to execute Floola, nothing happens.  See below:

 ```
me@computer:~/Desktop/Floola-linux$ Floola
bash: Floola: command not found
me@computer:~/Desktop/Floola-linux$ ./Floola 
./Floola: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

```

Any ideas?   Floola is listed as an executable.  I have the libstdc++6 package installed.

I had the same problem and fixed installing libstdc++5, just apt-get it ;)

---

### Post by Saraslife on 2009-11-10
> **jocko said:**
> I downloaded floola just to see what the problem is, and it seems to run fine for me.
Did you extract the file to your desktop (to a foler called "Floola-linux"?
Then, try this in a terminal:
```
cd ~/Desktop/Floola-linux
./Floola
```
Does it work?
If it doesn't is there any error message?
And what's the point of that program?
I generally don't trust webpages with that extreme amount of ads on them... "Shorten your URL"? What's that about?


I have the same problem with installing floola as Utnubuster but I get.
female@sarahLinux:~/Desktop/Floola-linux$ ./floola
bash: ./floola: No such file or directory

I have libstd 5 and 6. I downloaded the floola-linux.tar.gz and extracted it to the desktop. What is my next step?

---

