---
title: "Installing Software not in repositories"
date: 2006-12-29
forum: General Help
---

### Post by Ulysses on 2006-12-29
Hello,

I am a newbie and I need help.

Abiword is my word processor of choice. The version in Synaptic is old. The newest version is available for download. I downloaded it without any problem. I cannot install it.

There is an autopackage to download but that does not work for me. I get error messages telling me that the sites to download from are not available. I didn't think this was a problem because I figured if I could download the source software I could easily install it. No go.

I surfed and found a link to a site that says it has instructions to install anything in ubuntu, but the link is unavailable ; despite what seems like the free world telling me that it is the best instruction around (even tried a google search for a possible PDF that someone might have created). I checked the ubuntu document storage facility and there is nothing there that helps me.

So, my question is this ; how do I install software in ubuntu?

Help?

](*,) 


RAR

---

### Post by meng on 2006-12-29
Have there really been major improvements from version 2.4.4 to version 2.4.6?

Well if you insist on installing from source:
[www.psychocats.net/ubuntu/installingsoftware](www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Ulysses on 2006-12-29
Hello,

Uh....Not sure. I just wanted to be up to date. Latest and greatest.
Plus, it was an opportunity to learn how to install software in ubuntu
I've been pretty spoiled, being able to get all that I want just by searching the repositories. I only ever knew windows before and that was always pretty easy, y'know? Run the install.exe and it all happened kinda like magic. Sorry, but it's true.
And for all of the goodness and beauty of ubuntu, I wanted to see if it could do all that windows could do.

I'll click the link for psychocats and give it a whirl. Worse comes to worse, I work from the old version available through Synaptic.

Thanks for the quick reply. 

(I'm multi tasking this afternoon ; babysitting my daughter, watching season 2 of Columbo on DVD and trying to install software in ubuntu)

RAR

---

### Post by meng on 2006-12-29
As far as I can see, version 2.4.4 is available from Dapper repositories (2.4.5 in Edgy repositories), and 2.4.6 is the latest there is. Now of course a big part of Abiword is its ability to import Word .doc files, so if there have been great strides made in the last two releases, then sure it's worth going to this trouble. The problem with installing from source is that there may be several dependencies you need to install too.

---

### Post by Ramses de Norre on 2006-12-29
It's as easy in ubuntu as in windows: download the deb and double click it.
Or run sudo dpkg -i filename.deb.
The latter looks more difficult but gives you more options (and where is that opportunity in windows?).

It's only a little more complicated if you want to install things from source, you'll need to read the READ_ME and INSTALL files carefully and then probably run ```
tar -xzf filename.tar.gz
cd dir_name
./configure
make
sudo make install
```
but this all depends, some programs need less or additional steps (as will be described in the earlier mentioned files).

If you're new to this all I suggest you install a deb or even better: stick with the official repo.

---

### Post by Ulysses on 2006-12-29
Hello

```
tar -xvzf abiword_2.4.6.orig.tar.gz
```
That was no problem. Unzipped it all to a folder on the desktop
```
cd abiword-2.4.6
```
No problem there, either
```
./configure
```
That command gave me this error
```
bash: ./configure: No such file or directory
```

```
make
```
That command gave me this error
```
make: *** No targets specified and no makefile found.  Stop.
```

```
sudo make install
```
And that command gave me this error
```
make: *** No rule to make target `install'.  Stop.
```

And I know, I know. I could stick with the official version in Synaptic but I got this stuck in my head until I can get it to work.

I wonder if abiword has a version available that is specific to ubuntu? With a .deb file...
But when I check out the README files there is nothing specific that applies to ubuntu.

And I am really sorry about the MSWindows crack. It was uncalled for. It is just something that someone else would use against me if they were to create an argument why not to switch to Linux (even something as user friendly as ubuntu)

RAR

---

### Post by meng on 2006-12-29
Check you have build-essential
sudo aptitude install build-essential

Don't feel too bad about the Windows joke, it didn't cause offense.

---

### Post by Ramses de Norre on 2006-12-29
Seems like there is no configure, which is possible but strange..
Have you read through the READ_ME and INSTALL files? There should be a section about compiling which will tell you to run the make stuff and such and would mention any additional steps.

If it still wont work after installing build-essential: post the contents of the folder (ls -la .).

(And I wasn't offended by your comparison with windows, but I just couldn't let it to respond to it)

---

### Post by Ulysses on 2006-12-29
Hey

Yup. Did the build -essential thing before. Sorry. Forgot to mention it. I followed the instructions in this link

[http://www.psychocats.net/ubuntu/installingsoftware]("http://www.psychocats.net/ubuntu/installingsoftware")

The source code still did not want to install.

Mind you, when I went to the Abiword site and went to their file server and found the .deb file for ubuntu.

[http://www.abisource.com/downloads/abiword/2.4.6/Linux/Ubuntu/6.06/]("http://www.abisource.com/downloads/abiword/2.4.6/Linux/Ubuntu/6.06/")

It was a cinch from there on in. Just like MSWindows. :) 
And for the record, Abiword is an excellent word processor. Better than Openoffice ; not such a memory hog.

Now, can someone give me an exercise on what software I can install from source? Just as a test. 

Thanks, alot, folks. 

Regards,
RAR

---

