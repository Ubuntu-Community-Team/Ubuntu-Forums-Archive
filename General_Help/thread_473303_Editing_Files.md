---
title: "Editing Files"
date: 2007-06-13
forum: General Help
---

### Post by makemeegg on 2007-06-13
How can I edit files via the cmd line?  I have messed around with "vi" but I was wondering if there are more user friendly editors and what would the syntax be?

---

### Post by zvacet on 2007-06-14
**gedit**

for example if you want to edit file in your home folder

```
gedit /home/username/filename
```

but if you want to make changes in edited file

```
sudo gedit /home/username/filename
```

---

### Post by southernman on 2007-06-14
If you want to use gedit, please don't run gui apps without doing a gksudo, rather than sudo. It's (AFAIK) a security issue.

I also find vi (vim) a little over my head atm. So I use

> sudo pico <insert file name>

Once you make your changes to the file just do 

CTRL x to quit editing and close the file - then do a 
y or n to save the changes or not
and enter key a final time to keep the same file name in tact.

---

### Post by reclusivemonkey on 2007-06-14
joe
jove
jed
nano

Are all alternatives you can try. I seem to remember one had a drop down menu at the top, this would probably be the most friendly for you.

Although vi/vim has a steep learning curve, its well worth learning as its the one editor you can rely on being installed on just about any Unix based box you would come across. vimtutor will give you a good introductory guide. Good luck.

---

### Post by southernman on 2007-06-14
Thanks reclusivemonkey, for the tip... installing vim-runtime now to use the vimtutor.

---

### Post by reclusivemonkey on 2007-06-14
No problem =]

If you have a printer, a Vim cheat sheet may also be helpful;

[http://www.google.co.uk/search?q=vim+cheat+sheet&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.co.uk/search?q=vim+cheat+sheet&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

Although personally I've never found a cheat sheet that gave me everything I wanted as a new user; I keep meaning to create one myself but never quite get round to it!

---

### Post by southernman on 2007-06-14
Cheat sheet... roger that!  :)

---

### Post by hikaricore on 2007-06-14
> **zvacet said:**
> **gedit**

Excuse me if I missed something, but if the OP wants to edit files from the **command line** what purpose would gedit serve in this?

---

### Post by stchman on 2007-06-14
> **zvacet said:**
> **gedit**

for example if you want to edit file in your home folder

```
gedit /home/username/filename
```

but if you want to make changes in edited file

```
sudo gedit /home/username/filename
```

You only need sudo if root access is required.

---

### Post by zvacet on 2007-06-14
> Excuse me if I missed something, but if the OP wants to edit files from the command line what purpose would gedit serve in this?

How do you access your source list?

```
gksudo gedit /etc/apt/sources.list
```

And that is just one example.

> You only need sudo if root access is required.

Yes,but without sudo you are not able to make changes in the file.

Default text editor in Ubuntu is** nano**.

---

### Post by southernman on 2007-06-14
> **zvacet said:**
> How do you access your source list?

```
gksudo gedit /etc/apt/sources.list
```

And that is just one example.



Yes,but without sudo you are not able to make changes in the file.

Default text editor in Ubuntu is** nano**.
Both of you are right for your own scenarios... But, the example stchman used was for editing files in a users /home directory. No need for sudo in that instance.
:)

---

### Post by hikaricore on 2007-06-14
> How can I edit files via the cmd line?

^^

> **zvacet said:**
> How do you access your source list?

```
gksudo gedit /etc/apt/sources.list
```

And that is just one example.



Yes,but without sudo you are not able to make changes in the file.

Default text editor in Ubuntu is** nano**.

Unless the OP changed his message and I missed something he was asking for command line editors besides vi.

See where I'm confused that you keep bringing up gedit?

---

### Post by davidma777 on 2007-06-16
I'm having trouble using gedit or kedit from the command line under the kubuntu desktop. Under the ubuntu desktop -> terminal, gedit works fine by typing "gedit filename" from the directory where the file is located. Under the kubuntu desktop -> terminal, typing "gedit  filename" or "kedit filename" gets the following response:

  gedit <filename>
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

But then the file opens in whichever editor was used (gedit or kedit). I can use gedit this way but wonder why the error message comes up. How can I troubleshoot this problem?
Dave A.

---

### Post by davidma777 on 2007-06-20
I found the answer by searching with Google. The return which best hit the error message was Blind Squirrel with the entry:
 X Error: BadDevice, invalid or uninitialized input device 169
 June 2nd, 2007
In this article he referred to
[http://ubuntuforums.org/showthread.php?p=1762954](http://ubuntuforums.org/showthread.php?p=1762954)
which has a discussion of the error and the solution. I edited the xorg.conf file using nano, as advised in the discussion, to comment out the lines which mentioned the Wacom tablet device. I missed the last part of the discussion and could not boot into the GUI on restart. Restored xorg.conf by removing the # comment indicators, booted properly and reread the discussion. Further down in the discussion three additional lines also needed to be commented out. When I did this, booting worked, and the error did not come up when starting gedit from the command line.
No one answered this request. Furthermore, searching within the Ubuntu forums did not find the discussion mentioned above. Using Google did find it and put it at the top of the list indicating best match. The Ubuntu forums have so much information that it is hard to home in on a specific answer. The internal search helps to find general information but the user has to guess how best to make up the question to search with. (This verges on: you have to know the answer before you can figure out how to ask the question). Forum advice said to keep questions within threads which deal with the same issue. However, this may not be possible if the user doesn't have the time to read the large volume of material it may require and/or tinker with the search question. The fact that no one was willing to help   limits the forum's usefulness.
Dave A.

---

### Post by reclusivemonkey on 2007-06-20
> **davidma777 said:**
> 
No one answered this request. [...] The fact that no one was willing to help   limits the forum's usefulness.
Dave A.

Start your own threads when asking questions, you'll get better results. Its generally considered bad form to hijack a thread with your own questions.

---

### Post by davidma777 on 2007-06-20
reclusivemonkey said:
"Start your own threads when asking questions, you'll get better results. Its generally 
considered bad form to hijack a thread with your own questions."

Thank you for replying.

How do you start a new thread?
Also how do you quote a previous entry?

Dave A.

---

### Post by reclusivemonkey on 2007-06-20
> **davidma777 said:**
> 
How do you start a new thread?


Pick the most appropriate forum, then at the top of the threads lists, there is a "make New Post" button. Don't worry too much about forum selection, the mods will move your post if they deem it necessary, "General Help" is as good as any.

> **davidma777 said:**
> 
Also how do you quote a previous entry?


There is a "Quote" button as the bottom of each post. Clicking on that will show you the format.

---

### Post by notwen on 2007-06-20
+1 for pico and nano

---

### Post by davidma777 on 2007-06-20
> **reclusivemonkey said:**
> Pick the most appropriate forum, then at the top of the threads lists, there is a "make New Post" button. Don't worry too much about forum selection, the mods will move your post if they deem it necessary, "General Help" is as good as any.

There is a "Quote" button as the bottom of each post. Clicking on that will show you the format.

Thank you reclusivemonkey.
Dave A.

---

