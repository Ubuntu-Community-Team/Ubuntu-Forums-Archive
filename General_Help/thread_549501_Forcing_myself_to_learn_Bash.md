---
title: "Forcing myself to learn Bash"
date: 2007-09-12
forum: General Help
---

### Post by sci-fi guy on 2007-09-12
I have been wanting to learn to use the command line for a while, but a few days ago I came to the realization that I was simply too lazy to teach myself unless I made using the GUI more inconvenient than the terminal. But I didn't want to simply disable the GUI, because it would be incredibly difficult to switch cold-turkey.  I pondered over how to do this, and this morning I had an epiphany. First I copied the list of bash commands from [http://www.ss64.com/bash/](http://www.ss64.com/bash/). Then I made a blank image in GIMP the size of my desktop and put the whole list on that. Then I removed my icons, panel launchers, and the applications menu. Finally I added a terminal window to my startup sessions and a keyboard shortcut also to open a terminal. Now to do anything I at the very least have to type a program's name.

[[IMG]http://www.images.winupload.org/1189640224-Screenshot-small.png[/IMG]](http://www.images.winupload.org/1189632298-Screenshot.png)

Now I would appreciate any advice/comments the rest of the forum might have to further enhance my learning experience.

---

### Post by lambros on 2007-09-12
Wow! I love it! :KS

Here's a link to get you started: [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

Best of luck,
Lambros

---

### Post by sci-fi guy on 2007-09-12
How do I make a thumbnail on this page of the screenshot?

---

### Post by lambros on 2007-09-12
How to shrink that screenshot?  Well, let's do it from the command-line, why not?  :-)

First of all, you need a tool to work with images from the command-line.  ImageMagick is good for this, so let's install it:

```
sudo aptitude install imagemagick

```

If you get a password prompt, just type in your regular password and press Enter.  It will not be shown while you type it (not even as ***) but it will work, as long as you type it accurately.

Now you need to find the image you saved on your hard-disk.  I'll assume you saved it to your Desktop, and it's called "Screenshot.png"

```
cd Desktop
ls

```

Make sure your screenshot is shown in that list of files.  Now let's convert it.  This web-page explains how you can do it: [http://www.imagemagick.org/Usage/resize/](http://www.imagemagick.org/Usage/resize/)

The command will be something like this:

```
convert Screenshot.png -resize 640x480 Screenshot-resized.png
```

That should create a new, resized image in your Desktop folder.  You can open it with your default image-viewer with this command:

```
gnome-open Screenshot-resized.png

```

If all is well, hopefully you should be able to upload that new image, and edit your post to  change the link.

Lambros

---

### Post by lambros on 2007-09-12
Sorry, I don't know how to make a thumbnail that links to the full image.  At least I know how to make the thumbnail image - just change the '640x480' to something smaller! :-)  Hope someone else can help.

Lambros

---

### Post by sci-fi guy on 2007-09-12
I think I figured it out: insert the small image with URL tags to the big image. :o
... ... ... ... ...
... ... ... ... ...
Victory!

---

### Post by confused57 on 2007-09-12
Maybe this will help:
[http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/36936-howto-how-make-clickable-thumbnails-forums.html](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/36936-howto-how-make-clickable-thumbnails-forums.html)

---

### Post by sci-fi guy on 2007-09-13
Another question: How can I disable (not uninstall) nautilus so that I cannot be tempted to run it?

---

### Post by kh1116 on 2007-09-13
hey can you post that actual image on here, i'd like to use that too if you dont care

---

### Post by Matt Yun on 2007-09-13
> **sci-fi guy said:**
> I have been wanting to learn to use the command line for a while, but a few days ago I came to the realization that I was simply too lazy to teach myself unless I made using the GUI more inconvenient than the terminal. But I didn't want to simply disable the GUI, because it would be incredibly difficult to switch cold-turkey.  I pondered over how to do this, and this morning I had an epiphany. First I copied the list of bash commands from [http://www.ss64.com/bash/](http://www.ss64.com/bash/). Then I made a blank image in GIMP the size of my desktop and put the whole list on that. Then I removed my icons, panel launchers, and the applications menu. Finally I added a terminal window to my startup sessions and a keyboard shortcut also to open a terminal. Now to do anything I at the very least have to type a program's name.

You would probably like [tilda]("http://freshmeat.net/projects/tilda/?branch_id=55059&release_id=230637"):  "Tilda is a console application taking after such classic first person shooters as Quake, Doom, and Half-Life. It is a console with the ability to slide off of and onto the the screen when the user needs it with the click of a button."

Just do 'apt-get install tilda' and add it to your gnome session startup.  It's usually more convenient than having a console window, especially if you're working from reference materials in your browser.

Some bash tutorial sites:  

[Bash Programming - Introduction]("http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html")

[Aliens Bash Tutorial (beginners)]("http://subsignal.org/doc/AliensBashTutorial.html")

[Advanced Bash Scripting Guide]("http://tldp.org/LDP/abs/html/")

[Linux By Example:  Bash]("http://linux.byexamples.com/archives/category/bash/") (bash "recipes")

---

### Post by lambros on 2007-09-13
> **sci-fi guy said:**
> Another question: How can I disable (not uninstall) nautilus so that I cannot be tempted to run it?

Hmm... how exactly would you run it?  Typing 'nautilus' in the Terminal?  By removing your panels and icons, you've already foreclosed all other methods of running Nautilus, AFAICT.  So, you're worried you might be tempted to type 'nautilus' in the Terminal.  Well, here's a fun method of disabling that: Edit your .bash_aliases file:

```
gedit ~/.bash_aliases

```

Then add this line:

```
alias nautilus="echo \"I'm sorry Dave, I'm afraid I can't do that.\""
```

(If that's the last line, make sure there is a NEWLINE at the end.)  Save and exit.  Next time you open a Terminal, you'll be prevented from running That Evil GUI File Manager! :-)

Well, almost!  It's still ridiculously easy to run it, but you don't want to know, right? :-)

Lambros

---

### Post by sci-fi guy on 2007-09-13
> **kh1116 said:**
> hey can you post that actual image on here, i'd like to use that too if you dont care

What's your resolution? My laptop is widescreen, so the ratios would be off. I'll make another one. Also, how many pixels wide are your panels, where are the panels localed (top, bottom, left, right), and do you want an empty space for icons?

Thanks for all the Tutorials everybody!

---

### Post by sci-fi guy on 2007-09-13
> **lambros said:**
> ```
alias nautilus="echo \"I'm sorry Dave, I'm afraid I can't do that.\""
```

I love it! And you are right that I don't want to know. For now. Just don't die without telling me how to reverse it first.
Also, it was unable to find that file, so it created a new one. Did I miss something? (I haven't used aliases)

---

### Post by lambros on 2007-09-13
> **sci-fi guy said:**
> I love it! And you are right that I don't want to know. For now. Just don't die without telling me how to reverse it first.
Also, it was unable to find that file, so it created a new one. Did I miss something? (I haven't used aliases)

That's OK if it created a new one.  But there is another tweak you might need to do, so that it actually reads the .bash_aliases file.  Edit your .bashrc file:

```
gedit ~/.bashrc
```

and find the section that looks like this:

```
# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi

```

Uncomment those bottom three lines, by removing the '#' symbols.  That should take effect next time you open a Terminal.

Lambros

---

### Post by por100pre1 on 2007-09-13
> **sci-fi guy said:**
> I have been wanting to learn to use the command line for a while, but a few days ago I came to the realization that I was simply too lazy to teach myself unless I made using the GUI more inconvenient than the terminal. But I didn't want to simply disable the GUI, because it would be incredibly difficult to switch cold-turkey.  I pondered over how to do this, and this morning I had an epiphany. First I copied the list of bash commands from [http://www.ss64.com/bash/](http://www.ss64.com/bash/). Then I made a blank image in GIMP the size of my desktop and put the whole list on that. Then I removed my icons, panel launchers, and the applications menu. Finally I added a terminal window to my startup sessions and a keyboard shortcut also to open a terminal. Now to do anything I at the very least have to type a program's name.

Now I would like any advice/comments the rest of the forum might have to further enhance my learning experience.

Good learning strategy! :)

---

### Post by bodhi.zazen on 2007-09-13
:lolflag:

First, very small typo ....

it is "wget" not "Wget" ~ I know, I know, it is a very minor typo, but Linux is case sensitive so Wget will not work ...

The second one I should not tell you ...

If you want to run a command you have aliased enclose it in single quotes

'nautilus' for example :twisted:

/bodhi hides

Nice wallpaper. Would you mind posting a shot without the gnome desktop ? You can upload the raw image as an attachment or post the image rather then a screen shot ? Should look cool now that you know how to embed a smaller image in a link ...

Thanks in advance.

---

### Post by sci-fi guy on 2007-09-13
> **bodhi.zazen said:**
> :lolflag:Nice wallpaper. Would you mind posting a shot without the gnome desktop ? You can upload the raw image as an attachment or post the image rather then a screen shot ? Should look cool now that you know how to embed a smaller image in a link ...

Thanks in advance.

I'll pretend I didn't read the quotes part...

kh1116 asked the same thing and I have the same response: Sure, but since my laptop is widescreen, the ratios will be off unless you also have widescreen. I would be willing to make another one with the correct ratio if you tell me your screen resolution, the width of your panels (as well as how many panels you have and where they are located), and finally whether or not you want a blank column for icons.

---

### Post by lambros on 2007-09-13
> **bodhi.zazen said:**
> :lolflag:

The second one I should not tell you ...

If you want to run a command you have aliased enclose it in single quotes

'nautilus' for example :twisted:

/bodhi hides



Not to worry, Mr sci-fi guy, I have a solution for you that is quote-proof! :lolflag:

Edit your .bash_aliases file, and remove the alias for nautilus.  Put this instead:

```
nautilus()
{
  echo "I'm sorry Dave, I'm afraid I can't do that"\!
}

```

But it's still trivial to circumvent.  This is an arms race I can't win! :)

Lambros

---

### Post by bodhi.zazen on 2007-09-13
I am trying to resist entering into the arms race ....

Lets let sci-fi guy figure it out for himself :twisted:

sci-fi guy: Well, it would be used my many folks I assume, if you were going to go to the effort, why not post a standard (high) resolution like 1600x1200.

Others can always resize that ...

---

### Post by sci-fi guy on 2007-09-13
I am uploading it as the .xcf 'source code' so that everybody can move things to suit their desktop. It is 1600*1200. As it is, it allows for 30-pixel top and bottom panels, so those who shrink it should have a little leeway. Also, there is a 300 pixel empty space to the left for if you want icons.

And bodhi, I appreciate your self-control. Also, regading the typo, i know that wget is supposed to be lowercase. It was capitalized on the list and I simply cut-n-paste.

EDIT: As a side note, I am getting frustrated when I close a terminal window and the accompanying program is closed. Is there a setting I can toggle somewhere that will cause a terminal to close (or at least hide) when it is executing a program? Preferably something I won't have to apply to each individual window, such as %U.

---

### Post by bodhi.zazen on 2007-09-13
Gasp ... *Close the terminal*

Ya that is kind of a pain, you have a few options.

1. Start a program in a sub shell :

> {
(command &)
}

2. nohup

> nohup <command>

3. Use detach

dtach -c /tmp/com <command>

dtach -a /tmp/com

[list][*]You can use any name you like in place of "com"[/list]

4. Use screen.

[http://www.linuxjournal.com/article/6340](http://www.linuxjournal.com/article/6340)

[http://www.linuxjournal.com/articles/lj/0105/6340/6340t1.html](http://www.linuxjournal.com/articles/lj/0105/6340/6340t1.html)

[http://gentoo-wiki.com/TIP_Using_screen](http://gentoo-wiki.com/TIP_Using_screen)

Is that enough to get you going ?

(use the *path* Luke ...  #-o  )

---

### Post by sci-fi guy on 2007-09-13
Cool! To comprehend what you told me I simply had to look at my desktop ;). nohup works, and I am going to look into the last two now.

EDIT: On the first page of the [LinuxCommands]("http://www.linuxcommand.org/wss0010.php") script tutorial, he suggests editing my .bash_profile file. Where is it? Does it need to be created?

---

### Post by sci-fi guy on 2007-09-14
Figured out how to circumvent the nautilus alias: Open trash.

---

### Post by dscherry on 2007-09-14
If you've installed midnight commander (mc), you might set your nautilus alias to 'mc'.  (If you haven't installed it, check it out, it's a very powerful command line file manager).  Although mc isn't technically a bash command, it runs under bash, so it qualifies as a command line tool and doesn't rely on the GUI.

That way, you can type 'nautilus' to your heart's content, and you'll get something close enough to get the job done.  After a while, you'll find it's quicker to just type 'mc'.

food for thought...
Dan

---

### Post by Lord Illidan on 2007-09-14
Also, how about trying command line browsing? links2 or lynx?

---

### Post by bodhi.zazen on 2007-09-14
How about a new shell ? 

z shell (aka zsh) is awesome and significantly increases the power of the shell.

Also don't forget about tab completion.

[http://friedcpu.wordpress.com/2007/07/24/zsh-the-last-shell-youll-ever-need/](http://friedcpu.wordpress.com/2007/07/24/zsh-the-last-shell-youll-ever-need/)

[http://dotfiles.org/~Ryuzaki/.zshrc](http://dotfiles.org/~Ryuzaki/.zshrc)

The problem with zsh is you need a nice config file, .zshrc

See the second link. zsh supports all your bash aliases (you can add "source .bashrc" (without quotes) to .zshrc if you like to get started)

---

### Post by sci-fi guy on 2007-09-14
> **Lord Illidan said:**
> Also, how about trying command line browsing? links2 or lynx?

How well do Ubuntu Forums and Slashdot render?

I will look up all the programs suggested.

---

### Post by Lord Illidan on 2007-09-14
links2 handles ubuntuforums pretty well.. It will never compete with firefox, but it is handy if, say, X crashes.

---

### Post by finferflu on 2007-09-14
How about using a not-so-GUI window manger? I really like ratpoison, Xmonad, dwm and wmii, have a go with those ones, and you'll start using command line applications almost by instinct (since the use of the mouse will become superfluous) :D

If you decide to do so and need any help, don't hesitate to PM me ;)

---

### Post by sci-fi guy on 2007-09-14
the CLI window-managers work great!

EDIT: I think I figured out how to close a terminal when it's program is closed:
```
<command> && exit
```

Seems to be working.

EDIT 2: How do I cut & paste with the command line without using the mouse?

---

### Post by kh1116 on 2007-09-14
thanks for the background wallpaper, works great!

---

### Post by lambros on 2007-09-15
> **sci-fi guy said:**
> Figured out how to circumvent the nautilus alias: Open trash.

Heh heh! :grin: You'll just have to get rid of the Trash icon, then!

Lambros

---

### Post by lambros on 2007-09-15
> **sci-fi guy said:**
> 

How do I cut & paste with the command line without using the mouse?

If you want to copy/paste between the Terminal and another graphical app (like Firefox), you can use Ctrl-Shift-C to copy and Ctrl-Shift-V to paste.

As far as I'm aware, the Bash shell does not have any concept of a global "clipboard" that works between different Bash sessions.  The closest thing I can think of is: Bash's "history" function.  Hope someone will correct me if I'm mistaken :-)

Lambros

---

### Post by bodhi.zazen on 2007-09-15
There are many ways to copy-paste. 

Check out gpm ~ gpm allows you to use your mouse in a console :twisted:

Once gpm is installed (it is in the repos) :> Copying and pasting large blocks of text with a working mouse server is very easy. Simply highlight the text with the left mouse button (it will stay highlighted when you release the button), switch to a different terminal if you wish, position the cursor, and press the middle mouse button to paste the text where you placed the cursor.

See also this tutorial, although there are others : [http://linuxbasics.org/tutorials/using/working_with_plain_text_files](http://linuxbasics.org/tutorials/using/working_with_plain_text_files)

---

### Post by sci-fi guy on 2007-09-15
> **bodhi.zazen said:**
> There are many ways to copy-paste. 

Check out gpm ~ gpm allows you to use your mouse in a console :twisted:

Once gpm is installed (it is in the repos) :

See also this tutorial, although there are others : [http://linuxbasics.org/tutorials/using/working_with_plain_text_files](http://linuxbasics.org/tutorials/using/working_with_plain_text_files)

Actually, lambros' post is more of what I wanted, but I will keep this in mind;)

I am hoping to reach a point that I do not need a mouse at all (for times when it may be inconvenient, such as a lack of desk space or when the only alternative is the touchpad)

---

### Post by sci-fi guy on 2007-09-15
I need to take a break of a few hours from LinuxCommand.org to digest what I've learned, and thought this would be a good time to head in a new direction with CLI:
remote login.

Here's the situation: I recently gave my old system to my two youngest brothers and my sister (with Ubuntu on it, of course) and set them all up as administrators, since I didn't want to do update maintenance and such. But the brothers  have been abusing this power by demoting my sister to ordinary user. (with great power comes...something they are not mature enough to handle) So I logged on as one of the brothers. made both of them ordinary users and my sister the sole administrator (this was a week or two ago and I don't think they noticed yet. Out of sight, out of mind...) . This would be fine, but one of the brothers knows my sister's password and I can't persuade her to change it (she is rather attached to it for some reason) and he will be able to reverse this situation if he notices his lack of administrator privileges. So, to make a long story short, I want to login as my sister over the network, create a new administrator account (mine, with password unknown to brothers) demote my sister to ordinary user as well (she's okay with this) and use my account to maintain that system entirely from my computer. (apt-get update/upgrade and the like)

EDIT: I have almost reached an average of 1 post per day! (0.94 at present)

---

### Post by bodhi.zazen on 2007-09-15
> **sci-fi guy said:**
> I need to take a break of a few hours from LinuxCommand.org to digest what I've learned, and thought this would be a good time to head in a new direction with CLI:
remote login.

Here's the situation: I recently gave my old system to my two youngest brothers and my sister (with Ubuntu on it, of course) and set them all up as administrators, since I didn't want to do update maintenance and such. But the brothers  have been abusing this power by demoting my sister to ordinary user. (with great power comes...something they are not mature enough to handle) So I logged on as one of the brothers. made both of them ordinary users and my sister the sole administrator (this was a week or two ago and I don't think they noticed yet. Out of sight, out of mind...) . This would be fine, but one of the brothers knows my sister's password and I can't persuade her to change it (she is rather attached to it for some reason) and he will be able to reverse this situation if he notices his lack of administrator privileges. So, to make a long story short, I want to login as my sister over the network, create a new administrator account (mine, with password unknown to brothers) demote my sister to ordinary user as well (she's okay with this) and use my account to maintain that system entirely from my computer. (apt-get update/upgrade and the like)

EDIT: I have almost reached an average of 1 post per day! (0.94 at present)

ssh

[uwiki]SSHHowto[/uwiki]

[uwiki]AdvancedOpenSSH[/uwiki]

---

### Post by sci-fi guy on 2007-09-15
SSH ain't working. I get an error saying "no route to host". I tried pinging it, and got:
PING 192.168.1.5 (192.168.1.5) 56(84) bytes of data.
From 192.168.1.3 icmp_seq=1 Destination Host Unreachable
From 192.168.1.3 icmp_seq=2 Destination Host Unreachable
From 192.168.1.3 icmp_seq=3 Destination Host Unreachable...

---

### Post by bodhi.zazen on 2007-09-15
Is the computer on your LAN or are you accessing it across the internet ?

If across the internet you need to forward ports from any router (on the remote end) and use the internet IP, which you can find here :

[http://www.showip.com/](http://www.showip.com/) (of course you would need to do this on the remote box).

Also, most likely your IP provider uses dhcp, meaning the IP address will change. You will to check out something line dyndns.

[http://www.dyndns.com/](http://www.dyndns.com/)

Firewalls ?

---

### Post by sci-fi guy on 2007-09-15
LAN. And both systems have Ubuntu. No firewalls. Which computer needs the openssh server installed on it? I put it one being accessed.

EDIT: How can I tell a script to execute at a particular time in the distant future (say, the 18th of next month)? And I assume that if I use "; shutdown -P now" at the end of that script, the computer will turn off when everything else is done, right?

---

### Post by bodhi.zazen on 2007-09-16
You might want to start a new thread as I wonder how much help you will get with this question in a thread titled " Forcing myself to learn Bash" :lolflag:

Basically, yes the first step is to set up the computer you want to connect to, ie the server. Install and configure openssh. If you do not have a firewall, you might consider one as openssh opens a port (22 by default although I advise you change that).

You then need to resolve your ping issue as it does not sound as if you have disabled ping I would think this is then indicative of a network error. Of course is it possible some else installed (configured actually) a firewall ?

You then need to ssh in as a user on the server, ie "ssh user@ip_address". If the user name is the same on the server and client, you can skip that and just "ssh ip_address" (without quotes obviously).

Once that is done, you can forward single applications or even an entire desktop (with or without VNC). Follow the links I gave you.

---

### Post by sci-fi guy on 2007-09-16
You have a point. I'll make a new thread. Thanks!
EDIT: I feel like such an idiot. I was pinging the the wrong IP.  ssh works fine.

---

### Post by Sayers on 2007-09-16
Okay, heres how you learn shell. Install gentoo. Or create a virtual machine with gentoo or source mage and just learn how to compile packages by hand, I dont know it takes time to learn and more time to like it.

---

### Post by Sayers on 2007-09-16
Just don't load it switch to another screen like ctrl alt f1

---

### Post by sci-fi guy on 2007-09-16
> **Sayers said:**
> Okay, heres how you learn shell. Install gentoo. Or create a virtual machine with gentoo or source mage and just learn how to compile packages by hand, I dont know it takes time to learn and more time to like it.

I have a Gentoo Minimal iso in virtual machine (and a LiveCD iso that I haven't tried much), but couldn't even figure out how to install it.

---

### Post by Sayers on 2007-09-16
Read the doccument :P

---

### Post by Anzan on 2007-09-16
sci-fi guy, thank you for the bash GIMP file. It makes a nice desktop background.

---

### Post by sci-fi guy on 2007-09-16
An issue with wildcards: I wrote/plagiarized a simple bash script that identifies a typed character as either an uppercase letter, a lowercase letter, a number, or punctuation/special charager to practice if/then/else scripts. It seems that it would work, except that the shell is not recognizing my [A-Z], [a-z], and [0-9] wildcards as wildcards. It is interpreting that when I say I want it to check if the typed string equals [a-z], it will only be set as true if I typed out "[a-z]". What am I dong wrong?

---

### Post by lambros on 2007-09-16
> **sci-fi guy said:**
> An issue with wildcards: I wrote/plagiarized a simple bash script that identifies a typed character as either an uppercase letter, a lowercase letter, a number, or punctuation/special charager to practice if/then/else scripts. It seems that it would work, except that the shell is not recognizing my [A-Z], [a-z], and [0-9] wildcards as wildcards. It is interpreting that when I say I want it to check if the typed string equals [a-z], it will only be set as true if I typed out "[a-z]". What am I dong wrong?

Here's a method which might not be very efficient, but it is flexible.  Replace your line:

```
if [ "$char" = [A-Z] ]
```

with this:

```
if echo "$char" | grep -q '^[A-Z]$'
```

(and similarly for the other tests).

Your problem is: your [A-Z] doesn't do what you think it does.  The shell actually expands [a-z] depending on what files are in your current directory.

An example: I start out with an empty "test" folder, and I create some files with the "touch" command.  See what happens to [a-z] here:

```
ll@lambros-home:~/test$ ls
ll@lambros-home:~/test$ echo [a-z]
[a-z]
ll@lambros-home:~/test$ touch b c dd
ll@lambros-home:~/test$ ls
b  c  dd
ll@lambros-home:~/test$ echo [a-z]
b c

```

HTH,
Lambros

---

### Post by sci-fi guy on 2007-09-16
Well, it works. But the new line goes over my head. Could you please explain it?
EDIT: I have just finished Ktouch's Dvorak lessons and have made dvorak my default keyboard layout!  My posts should now be much shorter.

---

### Post by lambros on 2007-09-17
> **sci-fi guy said:**
> Well, it works. But the new line goes over my head. Could you please explain it?


It's the simplest method I know, to do what you asked.  If anyone knows a better way, please tell us!

Briefly:
"grep" is a tool that tests its input against a **regular expression**.  The ^[a-z]$ is a regular expression that matches a single lower-case letter (from the beginning to the end of the line).  I put it in single-quotes '..' to stop Bash from doing any funny-business with it.
The "echo" is simply to feed the input to "grep".  The '|' is the usual "pipe", to send the output from "echo" into "grep".
"grep" returns 0 (true) if the input matched, and non-zero (false) if not.  So the "if" simply tests the code returned by "grep".

Remember that your $char could hold more than one character, despite the name.  You didn't specify what should happen if the user typed in, say, "1a23".  I chose the regular expression to match only a single char, and no more.  But you could easily change this if you wanted.  You'd have to read up on regular expressions - it would take me too long to explain them here! :-)

Lambros

---

### Post by sci-fi guy on 2007-09-17
Ydato! Oops, I meant Thanks! Now I know what to look up.

---

### Post by sci-fi guy on 2007-09-18
Found a new way to circumvent the nautilus alias: browse with firefox. Although cli-browsing is more natural to me right now than either firefox or trash.

---

### Post by SpiritIsReality on 2007-09-19
howdy
great thread
thankyou all
IMHO... fluxbuntu looks like the answer

[http://wiki.fluxbuntu.org/](http://wiki.fluxbuntu.org/)

trails, amigos

---

### Post by sci-fi guy on 2007-09-19
Yet another circumvention: 'sudo nautilus'

---

### Post by sci-fi guy on 2007-09-19
> **fmat said:**
> howdy
great thread
thankyou all
IMHO... fluxbuntu looks like the answer

[http://wiki.fluxbuntu.org/](http://wiki.fluxbuntu.org/)

trails, amigos

Hmmm... Gotta try it out on VirtualBox until they have a 64-bit.

---

### Post by lambros on 2007-09-20
> **sci-fi guy said:**
> Yet another circumvention: 'sudo nautilus'

Effective, but not exactly safe! :-)  There's the usual caveat about not running programs as root if you can avoid it.  Also, the Ubuntu Gods would probably strike you down for using 'sudo' to run a graphical app! :evil:  Use 'gksudo' (or 'kdesu') instead.  If you changed a Nautilus preference whilst running it with 'sudo', I can't help wondering what kind of damage you'd do... :-k

Not that I want to scare you or anything! :-)
Lambros

---

### Post by sci-fi guy on 2007-09-20
I am aware of the danger. That's why I am not using that method.
New workaround: Insert a CD.

---

### Post by lambros on 2007-09-20
> **sci-fi guy said:**
> I am aware of the danger. That's why I am not using that method.
New workaround: Insert a CD.

Blimey!  I have to hand it to you - your workarounds are becoming ever more creative! :lolflag:  I never imagined I'd get sucked into a conversation about how **not** to use a bit of your system!

Well, I can't resist it <groan> - here's how to fix this little loophole:

```
gnome-volume-properties
```

Under the Storage tab, uncheck the box that says "Browse removable media when inserted".

But really, you'll kick yourself when you figure out just how easy it is to run nautilus.  The suspense is killing me! :-)

Lambros

---

### Post by sci-fi guy on 2007-09-20
I am removing the panels to slash the temptation of adding the menu back.

And lambros, I assume that the answer does *not* involve 'unalias' in any way, right?

EDIT: I CAN"T DELETE THE BOTTOM PANEL! TEMPTATION REMAINS!
I assume this is because the easiest way to add a new panel is right-clicking on an existing panel. But it is still frustrating!

---

### Post by sci-fi guy on 2007-09-20
SOLVED THE NAUTILUS QUESTION!
```
command nautilus
```

Now to commence kicking...
I put that wallpaper up for a reason.

---

### Post by Wolki on 2007-09-20
> **sci-fi guy said:**
> SOLVED THE NAUTILUS QUESTION!

You're pretty amazing, you keep finding solutions yet still miss the simple one... I've never heard of 'command' before, it doesn't have a man page, seems pretty obscure. Good find, I learn something new everyday.

Once you're familiar with the command line you might want to experiment with shells that have more features and cool stuff than the basic bash (which is great nonetheless). Two popular ones are zsh and fish.

(personally, I really love my nautilus and gui apps, but that doesn't mean I don't appreciate the shell - it's surprising how often it is extremely convenient once you know your way around some of the powerful stuff)

---

### Post by sci-fi guy on 2007-09-20
> **Wolki said:**
> ..you keep finding solutions yet still miss the simple one...

It was on my wallpaper. It wasn't the simple one? Must continue my search...
...
...
...
Found another one!
```
exec nautilus
```
I think I tried that one before, but it didn't work then.

And I do intend to experiment w/ other shells when I have become comfortable with bash.

EDIT: I posted a question on the last post of the preceding page, and I don't want it to get overlooked because someone hit the "Last Page" link. Basically, how can I get rid of the panels? I can remove one but I can't remove the other from the GUI.

---

### Post by Wolki on 2007-09-20
> **sci-fi guy said:**
> It was on my wallpaper. It wasn't the simple one? Must continue my search...
...
...
...
Found another one!
```
exec nautilus
```
I think I tried that one before, but it didn't work then.

Still rather complex, don't you think? 

also, exec has some other properties, the command you exec will replace the shell - quit that program and the shell will close as well.

> 
And I do intend to experiment w/ other shells when I have become comfortable with bash.

The basics are mostly the same, but they may offer advanced autocompletion, typo detection and other nifty things.

> EDIT: I posted a question on the last post of the preceding page, and I don't want it to get overlooked because someone hit the "Last Page" link. Basically, how can I get rid of the panels? I can remove one but I can't remove the other from the GUI.

gnome-panel requires you to have at least one panel open - and it makes sense too, if there were no panel you'd have a hard time getting one back. If you want no panel, you'd have to end the panel process; and stop it from restarting. I'm not sure this is even possible while running gnome, but you could try to remove it from session management using System -> Preferences -> Session.

I'd consider filling it with useful things like system monitors though, if your panel's full it's not as inviting to add the menu back.

---

### Post by sci-fi guy on 2007-09-21
Groan
](*,)   :-k   #-o

---

### Post by lambros on 2007-09-21
> **sci-fi guy said:**
> SOLVED THE NAUTILUS QUESTION!
```
command nautilus
```

Now to commence kicking...
I put that wallpaper up for a reason.

Ta-rah!!! :popcorn:

Now the cat's out of the bag, I can tell you the techniques I had in mind:

You could remove the alias (or function) with
```
unalias nautilus
```
or
```
unset nautilus
```

You could supply the full path:
```
/usr/bin/nautilus
```

You could start it in a sub-shell:
```
sh -c nautilus
```

And all the other methods that have already been posted.  (I've never heard of 'command', that's a new one on me)

Lambros

---

### Post by sci-fi guy on 2007-09-21
Great!
What'd you have in mind, Wolki?

And 'unalias nautilus' has been tried. But does not seem to be working.

---

### Post by Wolki on 2007-09-21
> **sci-fi guy said:**
> Great!
What'd you have in mind, Wolki?

```
/usr/bin/nautilus
```

It's beautifully simple as it doesn't involve any other command. And if you think about it, there's a lesson here - you can usually get what you want from a shell, you just need to make yourself really clear.

---

### Post by sci-fi guy on 2007-09-21
Am I correct in assuming that if I run
```
cd /usr/bin/; ls | less
```
that I will get a full list of all programs that I can run from bash?

Also, the 'less' command creates a *very* long list in one column. How can I make it's output look more like ls's (or, how can I make the ls output fully scrollable?)

---

### Post by Slim Odds on 2007-09-21
> **sci-fi guy said:**
> Another question: How can I disable (not uninstall) nautilus so that I cannot be tempted to run it?

Can someone tie my hands behind my back so that I'm not tempted to use the keyboard or mouse?

:lolflag:

---

### Post by Slim Odds on 2007-09-21
> **sci-fi guy said:**
> Am I correct in assuming that if I run
```
cd /usr/bin/; ls | less
```that I will get a full list of all programs that I can run from bash?

No, any program in the path can be run from bash

---

### Post by lambros on 2007-09-22
> **sci-fi guy said:**
> Am I correct in assuming that if I run
```
cd /usr/bin/; ls | less
```
that I will get a full list of all programs that I can run from bash?

Also, the 'less' command creates a *very* long list in one column. How can I make it's output look more like ls's (or, how can I make the ls output fully scrollable?)

It's actually 'ls', not 'less' that does this.  'ls' detects that its output is being piped through another command, so it behaves differently.  You can change this by adding the '-C' option to 'ls'.  Because 'ls' doesn't know the width of your terminal when piped through 'less', you may also want to add the option '-w 120' (adjust 120 to your needs).  There are probably other methods of doing pagination, too.

[edit] Just found out you can use the COLUMNS variable, instead of 120.  So the full command would be
```
cd /usr/bin/; ls -C -w $COLUMNS| less
```
[/edit]

But, as already pointed out, that shows you most commands, but not all of them.  It's missing all the stuff in /bin, /usr/games, and anywhere else on your path.  And it doesn't show you the shell builtins and keywords.  Nor does it show you your aliases and functions.

If you want to see all commands (everything), the simplest way is to hit TAB twice at the shell prompt.

To see all the shell builtins, type 'help'.  To get help on a builtin command, use 'help <command>'.  (It's a bit odd you have to use 'help' for a builtin, but 'man' for other commands).

As for 'unalias' not working: that command only works on an **alias**, it does not remove a **function**.  Use 'unset' to remove a function.  Remember my "quote-proof" solution?  That was an example of a function, not an alias.  So that's probably why 'unalias' isn't working in that case.

Lambros

---

### Post by sci-fi guy on 2007-09-22
Ah.
But double-TAB also gives me one column. Any way to change that?

---

### Post by lambros on 2007-09-22
> **sci-fi guy said:**
> Ah.
But double-TAB also gives me one column. Any way to change that?

Is this any use?
```
compgen -c | sort | uniq | column -c $COLUMNS | less
```

Lambros

---

### Post by sci-fi guy on 2007-09-22
Perfect.
Another topic: My sound card is not officially supported yet, but I can load a kernel module to enable sound. Unfortunately, I am testing Gutsy Gibbon and the kernel is updated somewhat frequently, so I have to re-apply the module. VirtualBox also needs a kernel module and so must be reinstalled every time the kernel is updated as well (fortunately no settings are lost) Anyways, to make a long story short, I want to automate the commands so that I just have to execute a single script after every kernel update and restart to get sound and Virtualbox working again. This is obviously a no-brainer, except that I would like to automate entering my password as well, or at least make it so that I must only enter my password when I first execute the script rather than halfway through when it gets to the 'sudo make install' point. Maybe a $password variable (and pray that I enter it right the first time)?

---

### Post by lambros on 2007-09-23
> **sci-fi guy said:**
> Perfect.
Another topic: My sound card is not officially supported yet, but I can load a kernel module to enable sound. Unfortunately, I am testing Gutsy Gibbon and the kernel is updated somewhat frequently, so I have to re-apply the module. VirtualBox also needs a kernel module and so must be reinstalled every time the kernel is updated as well (fortunately no settings are lost) Anyways, to make a long story short, I want to automate the commands so that I just have to execute a single script after every kernel update and restart to get sound and Virtualbox working again. This is obviously a no-brainer, except that I would like to automate entering my password as well, or at least make it so that I must only enter my password when I first execute the script rather than halfway through when it gets to the 'sudo make install' point. Maybe a $password variable (and pray that I enter it right the first time)?

Traditionally, with UNIX, you're not supposed to be able to programmatically feed a password to a security program.  These programs try very hard to make sure passwords are typed by a real person, and are not fed in by a script.

However, I looked at 'man sudo', and I noticed that it has the '-S' option to read its password from standard input.  So maybe you could use that?  Something like:
```
echo "$password" | sudo -S some-command-that-needs-root-access
```

As you point out, this isn't too great if you mistype your password.  Another idea is to use 'sudo -v' at the start of your script, like this:

```
sudo -v # prompt for password, until correct password is typed
compile-module-1
compile-module-2
sudo install-module-1 # hopefully, the 'sudo' timer is still active here
sudo install-module-2

```
Problem is, it relies on timing.  Your "sudo" privilege has to last long enough to survive compiling the modules.  Otherwise, you'll be prompted for a password again.  So you might want to setup your /etc/sudoers configuration to extend the timeout period.

I suppose you could run your whole script as root:
```
sudo ./my-script-to-install-kernel-modules
```

But that's horrible.  Compiling your modules as root will splatter your directory with root-owned files.  And it's doing too much as root.  That might introduce problems, if you were to modify your script and make a mistake.

Anyone else have any better ideas?
Lambros

---

### Post by sci-fi guy on 2007-09-23
The 'sudo -v' part will do nicely. This doesn't take *too* long.

---

### Post by bodhi.zazen on 2007-09-23
> **sci-fi guy said:**
> Perfect.
Another topic: My sound card is not officially supported yet, but I can load a kernel module to enable sound. Unfortunately, I am testing Gutsy Gibbon and the kernel is updated somewhat frequently, so I have to re-apply the module. VirtualBox also needs a kernel module and so must be reinstalled every time the kernel is updated as well (fortunately no settings are lost) Anyways, to make a long story short, I want to automate the commands so that I just have to execute a single script after every kernel update and restart to get sound and Virtualbox working again. This is obviously a no-brainer, except that I would like to automate entering my password as well, or at least make it so that I must only enter my password when I first execute the script rather than halfway through when it gets to the 'sudo make install' point. Maybe a $password variable (and pray that I enter it right the first time)?

You could write a script and execute it as root (ie sudo /path_to_script) or look at expect :

	[http://www.linuxjournal.com/article/3065](http://www.linuxjournal.com/article/3065)

	[http://www.linux.com/articles/56066](http://www.linux.com/articles/56066)

---

### Post by sci-fi guy on 2007-09-24
New kernel update arrived and the script worked fine.

---

### Post by sci-fi guy on 2007-09-26
How can I make a script execute far in the future? Without leaving the computer on 'til then?

---

### Post by lambros on 2007-09-26
I believe the 'at' command will do this (I've never used it myself).  You can use the 'cron' system if you need to schedule a regular task.

Lambros

---

### Post by sci-fi guy on 2007-09-26
By the man page's description, it looks promising.

EDIT: I just realized a nice way to keep all of my terminal windows organized: Hit Ctrl-Shift-T to open a new tab in the same window.

---

### Post by sci-fi guy on 2007-10-12
This is a new direction: since my last post I decided to try Kubuntu. I didn't like it that much but I decided to stick with it until Gutsy hit it's final release. But today, an update killed my GUI entirely. I figured I would install links2 and/or wait for an update that would fix the problem. That's when I realized I was missing an important piece of the puzzle when it comes to using cli: I have no idea how to connect to a network (wired or wifi) without the GUI tools. So now I am in the LiveCD reinstalling Gutsy's alpha version, frustrated at myself for overlooking this step. How can I attach to a network (preferably wifi) from the CLI?

---

### Post by markp1989 on 2007-10-12
> **sci-fi guy said:**
> I have been wanting to learn to use the command line for a while, but a few days ago I came to the realization that I was simply too lazy to teach myself unless I made using the GUI more inconvenient than the terminal. But I didn't want to simply disable the GUI, because it would be incredibly difficult to switch cold-turkey.  I pondered over how to do this, and this morning I had an epiphany. First I copied the list of bash commands from [http://www.ss64.com/bash/](http://www.ss64.com/bash/). Then I made a blank image in GIMP the size of my desktop and put the whole list on that. Then I removed my icons, panel launchers, and the applications menu. Finally I added a terminal window to my startup sessions and a keyboard shortcut also to open a terminal. Now to do anything I at the very least have to type a program's name.

[[IMG]http://www.images.winupload.org/1189640224-Screenshot-small.png[/IMG]](http://www.images.winupload.org/1189632298-Screenshot.png)

Now I would appreciate any advice/comments the rest of the forum might have to further enhance my learning experience.

would you be able to send me your background?

---

### Post by bodhi.zazen on 2007-10-12
> **markp1989 said:**
> would you be able to send me your background?

Look up, he posted it earlier on one of his previous posts ....

---

### Post by sci-fi guy on 2007-10-12
End of page 2

---

### Post by lambros on 2007-10-13
> **sci-fi guy said:**
> This is a new direction: since my last post I decided to try Kubuntu. I didn't like it that much but I decided to stick with it until Gutsy hit it's final release. But today, an update killed my GUI entirely. I figured I would install links2 and/or wait for an update that would fix the problem. That's when I realized I was missing an important piece of the puzzle when it comes to using cli: I have no idea how to connect to a network (wired or wifi) without the GUI tools. So now I am in the LiveCD reinstalling Gutsy's alpha version, frustrated at myself for overlooking this step. How can I attach to a network (preferably wifi) from the CLI?

For general networking from the CLI, you normally use programs such as "ifconfig", "ifup", "ifdown", and you would edit config files such as "/etc/network/interfaces", "/etc/hosts", "/etc/resolv.conf" and so on.

For WiFi, I have very little experience with that.  Best to look at the documentation.  Here's an index of WiFi docs to browse through - you might find what you're looking for in there.

[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

HTH,
Lambros

---

### Post by sci-fi guy on 2007-10-13
Thank you.

---

### Post by markp1989 on 2007-10-13
> **bodhi.zazen said:**
> Look up, he posted it earlier on one of his previous posts ....

> **sci-fi guy said:**
> End of page 2

sorry i didnt see that before, thanks

---

### Post by Ink-Jet on 2007-10-13
Surely a little self-restraint would be better than wrecking half your system?
Just make a terminal window start at boot, if you keep forgetting.

---

### Post by sci-fi guy on 2007-10-16
I found a pretty effective balance between learning CLI and having a GUI: use the JWM window manager. It requires manual configuration of the menus, does not have a desktop with icons, and as an extra bonus, it is snappy, too.

---

### Post by enchance on 2007-10-16
Are these all the commands? As in all bash commands? This is so cool!

---

### Post by sci-fi guy on 2007-10-16
I don't know about *all* BASH commands, but they are a lot of them.

---

### Post by Randulf on 2007-10-18
Like your style in how to learn bash!
This thread really inspired me to learn bash. Guess I have to use the same approach since I'm to lazy to learn if I have the GUI close at hand. Right now though I have my hands full in just learning Linux, btw no dual boot to be tempted to boot into windows : ).
Keep up the good work.

---

### Post by kolinab on 2007-10-18
Yes, this has been an entertaining thread to follow. Thanks to all!

---

### Post by sci-fi guy on 2007-10-24
How can I launch a graphical window within a tty session?

---

### Post by lambros on 2007-10-24
> **sci-fi guy said:**
> How can I launch a graphical window within a tty session?

I'm not exactly sure what you mean.  If you've got a graphical Terminal window open, and you want to open another one, you could use:

```
gnome-terminal & disown
```

Lambros

---

### Post by sci-fi guy on 2007-10-24
I mean that after hitting Ctrl-Alt-(F2-F6) and getting to a DOS-like screen, how can I run gui apps from there? I think I need to start X or something along those lines.

---

### Post by notwen on 2007-10-24
> **sci-fi guy said:**
> I mean that after hitting Ctrl-Alt-(F2-F6) and getting to a DOS-like screen, how can I run gui apps from there? I think I need to start X or something along those lines.

'startx' would start your DE, as far as starting a GUI window w/o being in a DE, I don't believe this is possible. =]

---

### Post by lambros on 2007-10-24
> **sci-fi guy said:**
> I mean that after hitting Ctrl-Alt-(F2-F6) and getting to a DOS-like screen, how can I run gui apps from there? I think I need to start X or something along those lines.

So the problem is something like this (using 'gcalctool' as an example)?

```
ll@lambros-home:~$ gcalctool

(gcalctool:12133): Gtk-WARNING **: cannot open display:  

```

Here's the solution:

```
DISPLAY=':0' gcalctool
```

HTH,
Lambros

---

### Post by sci-fi guy on 2007-10-24
> **lambros said:**
> So the problem is something like this (using 'gcalctool' as an example)?

```
ll@lambros-home:~$ gcalctool

(gcalctool:12133): Gtk-WARNING **: cannot open display:  

```

Here's the solution:

```
DISPLAY=':0' gcalctool
```

HTH,
Lambros

That's it. Although gcalctool didn't open until I switched back to TTY 7. I assume that is because you can only run X in one session at a time? That is what I gather when I tried 'startx'.

---

### Post by Yarbo on 2007-10-24
Hah, I love the idea.  So much so infact that when I get home I will be doing the same thing! 

bash ftw!

---

### Post by bodhi.zazen on 2007-10-24
FYI:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

[url=http://alecjw.googlepages.com/cubuntu-commandlineubuntu]Cubuntu - Command Line Ubuntu

 [/url]

---

### Post by lambros on 2007-10-24
> **sci-fi guy said:**
> That's it. Although gcalctool didn't open until I switched back to TTY 7. I assume that is because you can only run X in one session at a time? That is what I gather when I tried 'startx'.

OK, I'll try to explain (although my own understanding is certainly not perfect! :-).  When you run 'gcalctool' from within a tty, it doesn't know which X server to talk to, to tell it to draw the GUI.  This is normally set with the DISPLAY variable.  Try viewing the $DISPLAY from within your (Gnome) Terminal, and from within your Ctrl-Alt-F2 terminal.  Type this command into both terminals:

```
echo $DISPLAY
```

Notice the difference?  The $DISPLAY is set in your graphical terminal, but not in the other terminal.  That's why 'gcalctool' normally complains when you try to run it outside of X.  Which is why you have to explicitly say what DISPLAY to use.

You're certainly free to start as many X servers as you like.  You simply need to make sure they don't clash with one another.

So, when you type "startx" into the text-terminal, it complains - it can't start another X server on "display 0" because there's already an X server running on "localhost", using that particular numbered display.  Therefore, you have to use a different display number.  Try this command (in your text-terminal):

```
startx -- ':1'
```

If all is well, you will have two X servers running: one on 'localhost:0' and one on 'localhost:1'.  (The "localhost" part is implicit - it says the X server is running on your own PC, as opposed to another machine on the network).  You can switch between them by using Ctrl-Alt-F7 and Ctrl-Alt-F9.  At least, that is what happens on my system - your mileage may vary.

Assuming you've managed to get two X servers running, you can do all sorts of experiments.  Try "echo"ing the DISPLAY variable within a terminal on each server.  Try doing

```
DISPLAY=':1' gcalctool
```

from within your original X session, and see the window appear in the new X session!  (BTW, the single-quotes are to protect the ":1" from any special treatment by the Bash shell)

Maybe you can think of some uses for all this? :-)

Lambros

---

### Post by sci-fi guy on 2007-10-24
> **bodhi.zazen said:**
> FYI:
[url=http://alecjw.googlepages.com/cubuntu-commandlineubuntu]Cubuntu - Command Line Ubuntu
 [/url]

This is great!

---

### Post by sci-fi guy on 2007-10-24
> **lambros said:**
> *snip*

Pretty cool. When I started X under F2, it when straight to the desktop (although my RAM usage went through the roof)

And the most obvious and useful application for this I can think of for this is a multi-seat system, with one screen displaying one TTY window and one screen displaying another (and appropriately assigned keyboards and mice). I know it can be done, and have found tutorials, but I like to understand what is happening rather than cut 'n paste commands.

---

### Post by sci-fi guy on 2007-10-26
I have been trying to trim down my system's RAM usage, and I have made some pretty good cutbacks. For example, I uprooted Tomboy (20 MB) in favor of the Stickynotes applet (5 MB) and other similar replacements. But there is one thing that I can't figure out how to prevent from running: Nautilus (again). It sits there in System Monitor, using up 20-26 MB of RAM, probably because it displays the desktop.

It has no entry in "Sessions" (unless it is "User Folder Update", but I doubt it), so I was wondering how I can, at the very least, make another (lighter) File Manager the default.

---

### Post by sci-fi guy on 2007-10-28
Any way I can run two different window managers in different X sessions?

---

### Post by bodhi.zazen on 2007-10-29
Yes. You can either try something like Xnest : [http://www.xs4all.nl/~matto/xnest.html](http://www.xs4all.nl/~matto/xnest.html)

Or this : 

[http://ubuntuforums.org/showthread.php?t=271674](http://ubuntuforums.org/showthread.php?t=271674)

---

### Post by sci-fi guy on 2007-10-29
Perfect! Logging in and out for different WM's is a pain. This should make testing a lot easier.

---

### Post by bodhi.zazen on 2007-10-29
> **sci-fi guy said:**
> Perfect! Logging in and out for different WM's is a pain.

Yes, indeed

>  This should make testing a lot easier.

:twisted:

---

### Post by sci-fi guy on 2007-11-10
How can I launch a program on a particular face of the cube from a different face?

---

### Post by lambros on 2007-11-10
> **sci-fi guy said:**
> How can I launch a program on a particular face of the cube from a different face?

I had a quick look on the Gnome support forums and found this:

[http://gnomesupport.org/forums/viewtopic.php?t=12707](http://gnomesupport.org/forums/viewtopic.php?t=12707)

As suggested, you could try installing "wmctrl" and see if you can get that to do what you want.  Also, you could try looking in the forums or mailing lists for Compiz, since that is the program responsible for the cube.

If you're interested in learning more about the command-line shell, you might like to browse through the Ubuntu Programming Forum:

[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

The Bash shell is a programming language in its own right, so there are plenty of relevant discussion threads in that forum.

HTH,
Lambros

---

### Post by sci-fi guy on 2007-11-13
How can I make a launcher or something that will shut down the computer without asking for my password? JWM seems to only have a 'Logout' ability.

---

### Post by lambros on 2007-11-13
> **sci-fi guy said:**
> How can I make a launcher or something that will shut down the computer without asking for my password? JWM seems to only have a 'Logout' ability.

Normally, I'd use 'poweroff' if I were shutting down the PC from a command-line.  But that requires a password.  Try this instead:

```
gnome-power-cmd.sh shutdown
```

('shutdown' can be replaced with 'suspend', 'hibernate', or 'reboot')

Lambros

---

### Post by sci-fi guy on 2007-11-13
\\:D/
My preparations to make a full switch from gnome are almost complete! The only two obstacles I have left are:
1.  Starcraft does not launch correctly (can't see the opening screen but I can here it and click in the general area of the 'Exit' button)
2. JWM is not going to make people stop and say "What is that?!?" (at least not in a good way) because Compiz-Fusion does not work in JWM.

---

### Post by brennydoogles on 2007-11-13
> **sci-fi guy said:**
> the CLI window-managers work great!

EDIT: I think I figured out how to close a terminal when it's program is closed:
```
<command> && exit
```

Seems to be working.

EDIT 2: How do I cut & paste with the command line without using the mouse?

ctrl+shift+c for copy and ctrl+shift+v for paste

---

