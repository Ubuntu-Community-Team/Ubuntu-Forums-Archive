---
title: "RAR brute force attacker. Break it open!"
date: 2008-07-01
forum: General Help
---

### Post by Dark_Fire on 2008-07-01
Hey,

I have a old RAR file that I forgot the password of,

Is there any programme that could crack it for me? I know in windows I had one that could do zip files, at about 20,000 passwords a second...

Would be much appreciated!

---

### Post by Dark_Fire on 2008-07-01
Ok well I found one, but this is a split archive so it wont work.

But if anyone else wants to give it a try:
[http://rarcrack.sourceforge.net/](http://rarcrack.sourceforge.net/)

**Downloading:**
wget [http://superb-east.dl.sourceforge.net/sourceforge/rarcrack/rarcrack-0.2.tar.bz2](http://superb-east.dl.sourceforge.net/sourceforge/rarcrack/rarcrack-0.2.tar.bz2)

**Extracting:**
tar xvjf rarcrack-0.2.tar.bz2

**Dependencies:**
sudo apt-get install libxml2-dev

**Installing:**
cd rarcrack-0.2
make ; sudo make install

**Using it:**
rarcrack your_encrypted_archive.ext [--threads thread_num] [--type rar|zip|7z]

This one does about 600 Password a second. But it cant do split rar files it seems... It says archive corrupt...

Anyway, hope someone else finds this usefull.

Dark_Fire

---

### Post by g2g591 on 2008-07-01
for a split archive , just to cat filename.rar.part1 filename.rar.part2 (etc.) >>filename.rar . then run that on filename.rar . at least I'm pretty sure that will work

---

### Post by Dark_Fire on 2008-07-01
Thanks, it seemed to work... only problem now is it does 2 passwords every 6-8 seconds... It hasn't evin finished with the 2 digit one... It still has to do 2-0, a-z, A-Z... I dont have 3 years to get to 3 digits. lol...

anyway, is there a option 2 maybe?

---

### Post by Dark_Fire on 2008-07-01
Hey guys and guls,

I found something better... I think...

Well for the RAR it seems to work perfrectly, I still dont have my password thou... This one does 40 passwords a second. (on my PC)

Still not exactly what I had in mind... I know the windows version (it could only do zip/office files :'( sigh) It crashed your PC almost! It took like 10 seconds to respond to the "stop" command, and when you ran it for longer than an hour your PC was slower than ever! Only restart could fix it. lol.

But it moved! a minimum of 3,000 passwords a second. So im still looking for something better...

Here is the link to the other one I found.
[http://www.password-crackers.com/DOWNLOAD/crark31-linux.tar.gz](http://www.password-crackers.com/DOWNLOAD/crark31-linux.tar.gz)

Just simply Unzip it and run it.

enjoy

---

### Post by Dark_Fire on 2008-07-02
Well good news! Im at 4 digits already!

*sigh* This is gonne take forever aint it? :/

its at "i" now, 8 letters done, 18 to go, and I left it on all night long!

Talk about waisting time...

---

### Post by manfer on 2008-07-02
Do you know what a combination with repetition is?

Let's say the character set accepted by the passwords is:

{a,b,c,d,e,f,g,h,i,j,k,l,m,n,o,p,q,r,s,t,u,v,w,x,y,z,
A,B,C,D,E,F,G,H,I,J,K,L,M,N,O,P,Q,R,S,T,U,V,W,X,Y,Z}

52 different characters (for sure the character set would be greater than that, numbers, and some other characters accepted).

the combinations with repetitions for groups of:

1 character = 52
2 characters = 1378
3 characters = 24804
4 characters = 341055
5 characters = 3819816
6 characters = 36288252
...
16 characters = 1123787895356412
...

Can you answer yourself now? Are you wasting time trying to crack a password with that kind of brute force?

---

### Post by Dark_Fire on 2008-07-02
Wel, I know that my pas aint longer than 6 digets, and my previous brute force did 6 diget, aA1 and special chars in 15 min, 7 digets in 55 hours and 8 digets in 1 year.

I did a study on paswords, i know. Thats why im looking for one that runs faster. And maybe has a great dictionary support. I could do a word with random upper case and numbers to the length of like 15 chars in 20 mins.

Anyway, thanks for the reply.

Dark_Fire

---

### Post by tom66 on 2008-07-02
If there's a Windows version, you could try running it with Wine and see how well it works. Since wine isn't an emulator, if all goes well it should be as fast - or faster than - on native Windows.

---

### Post by phil0stine on 2009-03-27
I just used rarcrack for a split rar file, and for each part there is a different password. So far I have two different passwords returned by rarcrack.

The problem is, that these passwords don't work for their respective part files (I assumed they would work individually). 

So basically, if I spend the time to crack all the parts, I might still be out of luck? Anybody else having this problem?

---

