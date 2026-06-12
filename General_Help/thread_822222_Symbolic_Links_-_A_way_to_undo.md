---
title: "Symbolic Links - A way to undo?"
date: 2008-06-08
forum: General Help
---

### Post by mtreece on 2008-06-08
Hi,
[SIZE="5"]- > Beginning Story...[/SIZE]
     I've recently went out and bought a set of surround sound speakers, and well, since I have a laptop, I had to also purchase an external sound card... well after several days of attempting to get Ubuntu to recognize the sound card's existence, I can now finally get sound through the front-speakers, though I still cannot access true surround sound for when I play movies, etc.  I can, however, switch my speakers to a "Stereo" mode, and with that, it will direct certain frequencies to the sub-woofer (which makes a REALLY cool effect for listening to songs) :popcorn: .  The problem, however, was Amarok: my desired client for keeping my music.  Amarok wasn't wanting to recognize my sound card (which I think is set to be /dev/dsp1), and only allowed for me to select "/dev/dsp" (a flaw in Amarok that I've read about before), so like a complete and total genius, I ran the following command...

[SIZE="5"]- > And now, the problem...[/SIZE]
*mtreece@trhome:~$ sudo ln -s -f /dev/dsp1 /dev/dsp*

I ran this after I observed the "-f" to force the operation even though the file already exists (/dev/dsp), and didn't think about the possible after-effects.  I now realize that this has DELETED /dev/dsp (which I think is my built-in speakers), and while the good news is that Amarok now works like I want it to, I'm concerned that I won't ever be able to recover /dev/dsp...

Have I made a huge unrectifiable mistake?  Or... ?

I suppose I don't really need /dev/dsp, but I'm naturally a pack-rat, and thus naturally inclined to keep things (in case I could use it for another day :) ), so I would like to be able to recover /dev/dsp if necessary.

[SIZE="5"]- > What I have tried...[/SIZE]
Well, I read somewhere that "rm" would work just fine... and so I tried it... and it certainly removed it lol, but I'm now afraid that that has also removed any chance of me undoing the symbolic link.

Does anyone have any ideas or solutions for me?  Or... any information about symbolic links that might help?

Thanks in advance! :)

---

### Post by fsmithred on 2008-06-08
What did you rm? It makes a difference.

Think about this:
```
ln -s TARGET LINK_NAME
```
where TARGET is something that existed before you executed the command, and LINK_NAME is the symbolic link you create.

So, yes, you overwrote /dev/dsp with a symbolic link to /dev/dsp1. If you followed up with 'rm /dev/dsp' then you have deleted your symbolic link. Problem is, you now want a real /dev/dsp back. 

I think the solution is to use MAKEDEV, which is a script in the /dev directory that creates devices. Try 'man MAKEDEV'. Be careful! I don't have much experience with that command, and it's been a long time since I've used it, but I think you want to do:
```
cd /dev
sudo ./MAKEDEV dsp
```

Just to be safe, you could try this first, and it won't change anything:
```
sudo ./MAKEDEV -n dsp
```

---

### Post by mtreece on 2008-06-08
Hi fsmithred,

> What did you rm?

I rm'ed the /dev/dsp after I read that would remove the symbolic link.

I tried the ./MAKEDEV you suggested:

```
mtreece@trhome:/dev$ sudo ./MAKEDEV -n dsp
[sudo] password for mtreece:
udev active, devices will be created in /dev/.static/dev/
./MAKEDEV: don't know how to make device "dsp"

```

I tried that first to see what would happen, and since I'm also a dare-devil on the computer, I tried it without the "-n" option, and it still said it wasn't sure how to make device "dsp".
I'm guessing this is bad?

Nevertheless, I tried rebooting, and I think dsp came back (I had to redo the symbolic link for it to redirect output back to my surround speakers again), so I guess my problem is solved.

Thank you for your help though! :-).

Just for future reference, is there a way to make some sort of link to a file that is named another file - without having the named-file deleted first?... and if that's not possible, that would probably be a good idea to have created :-).  I'd work on that, but I've not yet developed my programming skills to such a level :lolflag:.

---

### Post by nlz on 2008-06-08
Is your question: i want to link to file x with a link names y?
then just type: ln -s /location/x /location2/y
then you get a link to the file with whatever name you give it (in this case 'y' but it can be everything).

try reading the manual, it's very helpful.

Just type: man ln

---

### Post by mtreece on 2008-06-08
> Is your question: i want to link to file x with a link names y?

Well, sort of... I'd like to be able to link "file x" with a link name that already exists as "file y".. that way any program that tries to reference "file y" will instead get "file x", but the problem is that using "ln" it will overwrite "y file" - which isn't always a good idea :).  And I'm not always capable of making a copy of "y file" before using the command (for whatever reason).

> try reading the manual, it's very helpful.
Yes, it's very helpful, but I think I'm a little bit dyslexic, so I can't always read the manual very well :-(.  But thanks for the suggestion :).

---

### Post by fsmithred on 2008-06-08
Rename or make a backup copy of file y before you create the link.

---

### Post by ibuclaw on 2008-06-08
Have you removed the erraneous link file yet?

If so, try rebooting. Usually all /dev/* modules get recreated on reboot.

And a good way of thinking about Symbolic links is this:

```
ln -s /path/to/TARGET /path/to/LINK
```
And only use the "-f" argument if you wish to edit an already existing target link.

[EDIT]
A small task you can carry out to get your head round it is this:

1) CD to the /tmp directory and create two files.
```

cd /tmp
touch fooA
touch fooB

```
2) Create a new symbolic link to fooA
```

ln -s fooA foolink

```
Now check that the link has been made successfully
```
ls -l foolink
```
And this should be your output
[PHP]lrwxrwxrwx 1 iain iain 4 2008-06-09 01:07 foolink -> fooA[/PHP]
As you can see, foolink is linked to fooA ("**foolink -> fooA**").

3) Now, to change the direction that foolink points too, we use -f to override the file.
```
ln -fs fooB foolink
```
Check that the link again with **ls -l**, and your new output should look like this
[PHP]lrwxrwxrwx 1 iain iain 4 2008-06-09 01:10 foolink -> fooB[/PHP]
Play about with it on dummy files until you get an accustomed to the way it works.

Regards
Iain

---

### Post by markbuntu on 2008-06-08
I usually do that sort of stuff with gksudo nautilus so I can see what's going on in the directories to make sure any link I make is not overwriting something I might need to get back later. It is also handy for changing permissions.

Nautilus also has that handy "make link" thingy so it is a simple click drag and drop. It is also very easy way to really mess things up so you need to be EXTREMELY careful.

I am trying to get away from the command line. It gives me bad memories from the ancient days when that was all there was. I mean, people wrote all these handy gui things so why not use them. Plus I am not such a good typist.

---

### Post by mtreece on 2008-06-08
Thank you everyone for replying! :)

Tinivole,
> If so, try rebooting. Usually all /dev/* modules get recreated on reboot.
Yes, thank you - I think this has worked just fine.  I guess for all other files (non-dev files) I will just have to see if I can make a copy.

And also, I will try the dummy-file suggestion; thanks for the tip! :guitar:

Markbuntu,
> I am trying to get away from the command line. It gives me bad memories from the ancient days when that was all there was. I mean, people wrote all these handy gui things so why not use them. Plus I am not such a good typist.
     Well, I kind of like the command-line.  I like GUIs too, but it's nice to be able to paste a few commands from a forum such as this to get a task done - as opposed to having to manually go through a bunch of programs to achieve the same result :).  But yes, I like Nautilus, it's a nice way to organize information (especially when you have several hundreds of files in a directory sometimes like I do hehe).

Once again, thanks everyone for the help!

---

### Post by Wilyhawk on 2009-05-26
The answer you are looking for to remove the link without deleting any files is this command:
```
sudo unlink /dev/dsp
```

---

