---
title: "new to ubuntu"
date: 2008-06-30
forum: General Help
---

### Post by ornovscot on 2008-06-30
I bought a book on basic ubuntu.  Still, the book illustrations don't match many of the images I find on the screen.  I have a dell computer with ubuntu already installed.

If I may, I would like to give a brief example.

On page 66 of Ubuntu Linux for non geeks there is an illustration of the Synaptic Package Manager, which I brought up on my screen by following the author's instructions.

But when I selected Settings near the upper left hand part of the screen and then selected Repositories I did not see the screen that appeared on page 68, Figure 5-2.


I am wondering how I can teach myself some of these concepts if the images appear in the book appear different than those on the screen of the computer.

In other words, I can't make the changes the author recommends.

Please note I did updates, but the discrepancy in the images continues.

Does anyone have any general suggestions about this situation.  Is there something wrong with my computer, perhaps?

Thank you in advance.



I would appreciate any suggestions.

Thank you

---

### Post by iaculallad on 2008-06-30
> **ornovscot said:**
> I bought a book on basic ubuntu.  Still, the book illustrations don't match many of the images I find on the screen.  I have a dell computer with ubuntu already installed.



I would appreciate any suggestions.

Thank you

Usually, images/pictures drawn on book pages may look different with your current setup. That is, if you're using a later version of Ubuntu and the books describing earlier version (vise-versa). Just remember that everything is still the same, virtually. From terminal commands, configuration files, filesystem hierarchy, and applications to name a few.

Try using Google and the forum instead, it's much updated than using a book.

---

### Post by 4t0m1c_w07f on 2008-06-30
Check what version the book was made for as new improvements to ubuntu have been made with new versions. There are also plenty of online e-books on ubuntu.

---

### Post by iaculallad on 2008-06-30
> **ornovscot said:**
> On page 66 of Ubuntu Linux for non geeks there is an illustration of the Synaptic Package Manager, which I brought up on my screen by following the author's instructions.

My suggestion for you with regards to illustration problem is to learn using the terminal, with just a few keystrokes, you could open your Synaptics Package Manager.

```
gksu /usr/sbin/synaptic
```

> **ornovscot said:**
> But when I selected Settings near the upper left hand part of the screen and then selected Repositories I did not see the screen that appeared on page 68, Figure 5-2.

To open your Repository or Software Sources window, you could input the command below on your terminal window.

```
gksu /usr/bin/software-properties-gtk

```

The terminal will always be a good friend when using Ubuntu.

---

### Post by ornovscot on 2008-06-30
Thank you much.  I tried to buy the most up to date book.


But perhaps I could ask one question about what I found.

In the book there is a section called Adding APT Repositories via Synaptic (that is, I'm trying to learn Synaptic for the first time).


For instance, the author recommends taking this pathway:

System menu->Administration->Synaptic Package Manager.

I was prompted to type in my password, which I did.  Doing that successfully brought up the Synaptic Package Manager.  That was fine and looked the way it did in the book.



In order to do something in relation to the APT Repositories via Synaptic, he instructed that the reader go to Synaptic Settings and then select Repositories.  I did these things first by going to the category of Setting near the top of the window that reads Synaptic Package Manager and then by selecting repositories.


For me what appeared was a window that read Software Sources.

The tab already open is called Ubuntu Software.  There are about 5 downloadable form the Internet; some are checked.

But I can't follow the author's instructions because the image he shows in his book is called Software Preferences, and it looks quite a bit different with an Add button.  


The image I brought up read Software Sources and didn't have an Add button.


I'm sorry for a long post.  I wanted to give an example of what seems to be hindering my progress.

I know the book is going to be different in some ways, although I bought the latest edition of the book at the same time I bought the Dell Ubuntu computer.

Earlier today I did the updates as well.

Any help would be appreciated.  Thank you for your patience.

---

### Post by ornovscot on 2008-06-30
For iaculallad:

Thank you so much for providing the commands to type into the terminal window, and they worked.

At the same time, though, they shwoed the same windows I obtained when I went to System menu->Administration->Synaptic Package Manager.

In other words, regardless of how I bring up these windows, the latter appear in such a way that I can't follow the instructions of the author.

For example, he wrote, "To activate the universe and multiverse repositories, scroll down the list of repositories in the main pane (Under the word Channels) and then check the boxes for all of the entries followed by Binary.

After you've done that, click the Add button, and once the Add Channel Window appears, check the boxes next to Community maintained (Universe) and Non-free (Multiverse).  After that, click the Add button to save your changes and close the window.


As I wrote above all I could see was a window called Software Sources that read Downloadable from the Internet with a series of checked categories, like Canonical supported Open Source software (main), etc.

Then there was an area called Download from Main server in a drop down menu.

---

### Post by iaculallad on 2008-06-30
From the news I read before, Dell products came pre-installed with Ubuntu Hardy (correct me if I'm wrong in here). So the book that you bought might be using an older version of Ubuntu.

Maybe, the author is referring to the "Third Party Software" tab when he/she said "Software Preferences". This is the option from where you could configure third party repository site to be used in your application download and application update.

-Put down the book instead and try to explore the one installed on your system. If you have any problem with regards to a certain application, try googling instead. This way, diagrams presented won't mess up your head.

---

### Post by VMC on 2008-06-30
Remember these are referred to as GUI interfaces. Just keep going, and do what is asked and even though the interface isn't exactly the same try and figure out the similarities that do exists.

Does it say in the beginning of the book what the name of ubuntu it is based on?
I don't recall you mentioning wha version is installed on your Dell.

I'm sure the author will get into Terminal commands and there it show look the same.

---

### Post by ornovscot on 2008-06-30
Thank you.  I agree with you about not relying a book.

Since I'm brand new to this, and I can't afford paid software support, I thought I would try to learn some basic concepts in the book I purchased.

For the most part, the simple commands and other simple maneuvers involving placing and removing icons in the panel are tasks the book has helped to learn.


But the other parts of the book are in discrepancy with the computer as it is.

I could go to the forum and ask for help, but I dont't even know many of the terms and thus how to ask questions.  So I thought reading a book would give some understanding so I could proceed from that point.


I tried a command like sudo ooffice -writer %U and pressed enter.

The Open Ofice.org launcher appeared, with the blue line going across, as if the program would successfully launch, but then it was interrupted by warning message that read /home/charles/%U does not exist.  Of course, my username is charles, and charles works with simple commands like whoami ls  and the like.  But it doesn't when I tried to combine sudo with a file name of a software alread in the computer (I tried Open Office writer software without the terminal window earlier simply by clicking onto its icon, and it opened without difficulty).


I am very sorry for the long posts; I just wanted to present the problem as I've ecnountered it.

Even though I can't afford it, I might have to use my credit card and call the number in London, and ask Damian to open an account.

Honestly, other than reading a book and doing a few things on my own or even reading forums, I think I'm going to need to get paid support.

---

### Post by iaculallad on 2008-06-30
I'd say, you don't need to hire for paid support. The forum is still the best place to learn. Try to post you questions/queries and member's will always be happy to tell solutions, advises, or relate you to another thread that has similar problem to what you posted. Just be patient to wait and at the same time try to scan the book for new ideas/terminal-commands you can learn and apply it.

---

### Post by aktiwers on 2008-06-30
Yeah throw the book away and ask all your questions here on the forums (or in the beginners section) and google :)

---

### Post by VMC on 2008-06-30
> **ornovscot said:**
> 
Even though I can't afford it, I might have to use my credit card and call the number in London, and ask Damian to open an account.

Honestly, other than reading a book and doing a few things on my own or even reading forums, I think I'm going to need to get paid support.

Unless this is urgent, why not just enroll in an adult computer class. Go to your local library and browse through the computer section. Join a local Linux Users Group. Maybe one in your neighborhood. The options are endless. 

Just take it slow and easy. Whats the hurry. And besides library are great places to meet people. How about computer swap meets. Google around for this stuff on the internet. You would be surprised at what shows up!

---

### Post by bunnieofdoom on 2008-06-30
> **ornovscot said:**
> Thank you.  I agree with you about not relying a book.

Since I'm brand new to this, and I can't afford paid software support, I thought I would try to learn some basic concepts in the book I purchased.

For the most part, the simple commands and other simple maneuvers involving placing and removing icons in the panel are tasks the book has helped to learn.


But the other parts of the book are in discrepancy with the computer as it is.

I could go to the forum and ask for help, but I dont't even know many of the terms and thus how to ask questions.  So I thought reading a book would give some understanding so I could proceed from that point.


I tried a command like sudo ooffice -writer %U and pressed enter.

The Open Ofice.org launcher appeared, with the blue line going across, as if the program would successfully launch, but then it was interrupted by warning message that read /home/charles/%U does not exist.  Of course, my username is charles, and charles works with simple commands like whoami ls  and the like.  But it doesn't when I tried to combine sudo with a file name of a software alread in the computer (I tried Open Office writer software without the terminal window earlier simply by clicking onto its icon, and it opened without difficulty).


I am very sorry for the long posts; I just wanted to present the problem as I've ecnountered it.

Even though I can't afford it, I might have to use my credit card and call the number in London, and ask Damian to open an account.

Honestly, other than reading a book and doing a few things on my own or even reading forums, I think I'm going to need to get paid support.


Well let me start by saying, welcome :). your problem with %U, could just be your terminal not reading the short-hand, try making an dir in your /home/charles folder with mkdir /home/charles/oodocs

then try your previous command  sudo ooffice -writer /home/charles/oodocs, and tell me if your problem persists. 

I always find it helpful to enter directories by hand as shortcuts usualy always break my crap.

Hope this was helpful

---

### Post by katiad on 2008-06-30
> **ornovscot said:**
> 
I tried a command like sudo ooffice -writer %U and pressed enter.

The Open Ofice.org launcher appeared, with the blue line going across, as if the program would successfully launch, but then it was interrupted by warning message that read /home/charles/%U does not exist.  Of course, my username is charles, and charles works with simple commands like whoami ls  and the like.  But it doesn't when I tried to combine sudo with a file name of a software alread in the computer (I tried Open Office writer software without the terminal window earlier simply by clicking onto its icon, and it opened without difficulty).

There really isn't any need to use the command line to open Open Office - as you noticed, it works fine just clicking on its icon. Also, when using Open Office, there shouldn't be much of a need to do so as the super user - (aka: using sudo to preface the command). The problem you encountered, where it's trying to find /home/charles/%U is that it's not having trouble finding your username, it's having trouble finding a file named %U, which is what your command attempted to open. There is no file named %U in your home directory, so it gave you an error. 

:)  Might I ask what you were attempting to open when you used this command, and why you used sudo for it?

---

### Post by aktiwers on 2008-06-30
Ooops.. just read your entire post.. Sorry.

I would still say you would be better off asking here on the Forums.

Just post your questions like you just did. Tell us why you want to open ooffice -writer with sudo and not just without. Explain what you don't understand, and people here will explain it for you :)

---

### Post by mempman on 2008-06-30
Did the book you bought come with an accompanying cd, which may contain the version of ubuntu that the book was specifically written for.  Also, in the preface or the backcover of the book, the author would have completely indicated the exact OS that the book was written with/for - whatever. 

Although there may be some discrepencies, I'm sure you'll be able to plug away and figure stuf out.  

And remember, if you aren't frustrated...you aren't learning.

---

### Post by bryncoles on 2008-06-30
is this what you are reading?

[http://books.google.co.uk/books?id=R41wjofxG_kC&dq=ubuntu+linux+for+non+geeks&pg=PP1&ots=c-s8WtN6bF&sig=BnRwGKJHobzSDevI2GZybHyyT6E&hl=en&sa=X&oi=book_result&resnum=1&ct=result](http://books.google.co.uk/books?id=R41wjofxG_kC&dq=ubuntu+linux+for+non+geeks&pg=PP1&ots=c-s8WtN6bF&sig=BnRwGKJHobzSDevI2GZybHyyT6E&hl=en&sa=X&oi=book_result&resnum=1&ct=result)

(sorry thats a long ulr...). if so, i noticed its copyright 2006. ubuntu adheres to a six month release cycle, so if you're on the 2006 edition you'd be what, four releases behind?

this is a good thing though - as it means you can know what you're supposed to do, what your supposed to achieve and roughly how to do / achieve it (though gui's will have moved on slightly since the book was published). 

dont worry about the discrepancies between what you see on the page, and what you see on your computer. understand the principle behind what you are doing, and you will learn how to use your computer, rather than how to add a repository to the 6:4 version of ubuntu (we're on 8:4 now). 

if you find you cant apply something from the book to the system you're using... well, just come here and ask!

oh - and i forget who mentioned it, but dell's still come with 7:10 - gutsy gibbon at the moment. i just bought one and upgraded to hardy - flawlessly! ;-)

hope you enjoy your time with ubuntu!

---

### Post by stalkingwolf on 2008-06-30
I have the same book. I found it to be a great book. It is a 
Mark1mod0 book.  The problem is it is based on Ubuntu 7.04
(disk included). If your dell has 8.04 the book is 2 generations behind.  Most of the exercises and examples work the same (allowing
for the change in terms). I have not tried them on 8.04 yet because
I have a resolution problem with 8.04.

This is the only Linux "how to" book that I have actually read 
cover to cover.  The author uses a light and amusing style that
makes it fun to read.

perhaps taking a look at Ch.8 Simple Kitten Ways (getting to know the Linux terminal and command line)would help.




Free the Fish.

---

