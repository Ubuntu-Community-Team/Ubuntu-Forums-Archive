---
title: "&quot;gksudo/gksu -k&quot;?"
date: 2007-09-04
forum: General Help
---

### Post by nvteighen on 2007-09-04
Hi! A question:

Do gksudo and gksu have a "kill" parameter like sudo ("sudo -k") that explicilty terminates the timeout? I like to use that sudo's feature... don't know why, actually, but sometimes I like to know that, no matter how much time has passed yet, I know I'll be prompted for the password again.

If gksudo and gksu don't have that, wouldn't be nice to implement it? I mean, along with the 15 min. timeout, to give the option to explicitly terminate them.

---

### Post by peetbull on 2007-09-04
The man-page for "gksudo" does not describe a functionality like "-k" as in "sudo".

But, gksudo is based on sudo to execute. 

So, if you are able to reset the password for sudo, this reflects on gksudo.

The following steps will help you create a "gksudo" variant that, no matter when you entered the su-password, it will ask for it. In other words, "you expilicitly terminate the timeout". ;)


_ Step 0_: Preparation

We are about to set bash shell recognize a new virtual command as an alias based on two existing ones.

But before we proceed, we might need to activate a preconfigured setting that will allow us to create user-specific aliases.

Edit "~/.bashrc" with your favourite editor. E.g. type in terminal :

gedit ~/.bashrc &

Find a commented line like this:

# Alias definitions

And below you should find three lines like:

#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi

Remove the leading hashes (#) from the lines, to activate them. They now should look like

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

If the hashes are already removed then just do nothing and go to Step 1.

Save the file.

Now we are ready to either create, or edit our aliases file with name ".bash_aliases" under our home root.


_Step 1_: Edit "~/.bash_aliases" environment settings file

Use your favourite editor to open the file. E.g. type in terminal "gedit ~/.bash_aliases &"
(note the dot leading the filename, it's a "hidden" file)

This file may already contain settings, or it may not currently exist. If it doesn't exist, it will be created upon saving.

Go to the end of file and read next step!


_Step 2_: Write an "alias" that terminates the timeout and calls "gksudo", forcing password entry.

At the end of your ".bash_aliases" enter the following line:

alias gksudo_k="sudo -k; gksudo"

With this line you tell system, that when you login (this is assumed because you are editting your ".bash_aliases") you have a virtual command by name "gksudo_k" that what actually does, resets password timeout "sudo -k" and then executes "gksudo".

As you can imagine, "gksudo_k" name is just an example, that reminds "gksudo" and "-k" sudo's parameter. You can substitute "gksudo_k" with an other name you might like.

(Note the underscore in "gksudo_k". I could have used a dash, making it "gksudo-k" but it would seem like a parameter and maybe it would be confusing because "gksudo -k" is already a defined functionality with different kind of results.)

Save ".bash_aliases" and finalize your brand new nuclear experiment with the last step.


_Step 3_: Register ".bash_aliases" changes

The settings of ".bash_aliases" must be registered in the environment. In a terminal, enter the following:

source ~/.bashrc


_Verification_: Is everything OK?

Use "gksudo gedit" and provide a password to open gedit as a super-user. 

Then close it and try the same command once more. This time it shouldn't ask for the password and should load gedit instantly. Password-timeout is already "running".

Now use our new 'command': gksudo_k gedit.
The password timeout is overriden and asks for a password, once more! From now on, no matter how many times you may have used "sudo", "su" or "gksudo", "gksudo_k" will force a password dialog to appear.

And remember that "gksudo_k" can have exactly the same parameters as "gksudo".

---

### Post by nvteighen on 2007-09-04
Hmmm... Actually, I was asking about the graphical sudo that works without the terminal, but your idea is that good that I'll also check it out! Thanks! :D 

What I meant was this: For example, when I open Synaptic through the menus and then, if I type "sudo -k" in Terminal, I still can enter Synaptic without any password until time is out. (now my doubt is if that really is gksudo or something else that escapes control by sudo?).

---

