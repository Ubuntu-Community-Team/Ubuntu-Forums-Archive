---
title: "[SOLVED] how to delete 400000 files? :-("
date: 2007-10-03
forum: General Help
---

### Post by marlinman on 2007-10-03
I tried out ghex's "Save as html" command earlier. I had a 100Mb file open and to my dismay about 400,000 html files were duly created on my Desktop. (Needless to say, this was not what I expected to happen!). Using "rm" to get rid of them is no good as I can only do about 1000 of them at a time thanks to an error of the form "too many files". What else can I try?

---

### Post by fdrake on 2007-10-03
sudo rm -R ./Desktop/*

copy the files u need on your home folder

---

### Post by superyounan1 on 2007-10-03
rm -R  will erase everything on the desktop, even folders.

consider:```
rm *.html
```

---

### Post by eph1973 on 2007-10-03
That's quite a lot of files!  superyounan1's suggestion is far better for 2 reasons:
It will only delete the HTML files on your desktop (provided you did not have an earlier HTML file on your desktop that you wanted to save), without going through everything in your Desktop without recursively going into any folders you have and deleting everything out of there, also.

The second reason is that you should own all the files on your desktop, and it's not a real good habit to sudo every command you do, to prevent accidentally doing something you didn't mean to do while you are the "superuser".

---

### Post by fdrake on 2007-10-03
unless the .html files don't have attached files on a separate folders like they usually do and are owned by the user, then i agree with the previous suggestion.

---

### Post by marlinman on 2007-10-03
Appreciate the suggestions, but like I said:

"Using "rm" to get rid of them is no good as I can only do about 1000 of them at a time thanks to an error of the form "too many files"."

So execing "rm *.html" from the Desktop directory throws an error. I guess I could write a batch file to remove the files 1000 at a time but that would stretch me quite far and I'm sure there's an easier way!

---

### Post by superyounan1 on 2007-10-03
oh i didn't realize 'rm' had a file limit, i guess i never had to delete so many files. Sorry i didn't read carefully.

a quick script should work, make a file, use a simple terminal text editor like 'nano':

```

cd ~/Desktop
nano cleanDesktop

```

paste this
```

#!/bin/bash
for X in *.html
        do
                rm "$X";
        done

```

press CTRL+O to save, CTRL+X to exit 'nano'

make the text file an executable script, lets say you called it "cleanDesktop",
```
sudo chmod 755 cleanDesktop
```

now execute the script
```
./cleanDesktop
```

---

### Post by eph1973 on 2007-10-03
> **fdrake said:**
> unless the .html files don't have attached files on a separate folders like they usually do and are owned by the user, then i agree with the previous suggestion.
Usually, the only reason you get attached files with .HTML is that you saved a web page, so all the little pictures on the web page has to be saved along with it, so the page will view correctly when you go back to it.  In this case, since it was ghex that did it, there shouldn't be any picture type files along with it (just text), so that shouldn't be an issue.

That bash script should be the ticket.

---

### Post by marlinman on 2007-10-03
Thanks for your idea superyounan1 - alas the script ran for a while then I got a "fork: Cannot allocate memory" msg and was returned to prompt. I'm running feisty in a virtual machine with 512Mb of RAM on a host with 2Gb - would upping the memory to the VM and trying again be worthwhile?

---

### Post by eph1973 on 2007-10-03
OK, new script here.

This is a perl script.

Same story, open gedit, or something to that effect, copy and paste this.  Then save it.  Then do the chmod 755 (filename) to it.
```

#!/usr/bin/perl -w

use strict;

for(@ARGV){
  unlink $_;
}

```Then, run it like the rm command, so if you saved it as "cleanup", and it was in your desktop directory, you would type the following to run it:

```
./cleanup *.html
``` Hope this works for you

---

### Post by dcstar on 2007-10-03
> **superyounan1 said:**
> oh i didn't realize 'rm' had a file limit, i guess i never had to delete so many files. Sorry i didn't read carefully.
.........

This is an "ancient" problem in Unix/Linux:

[http://www.gnu.org/software/coreutils/faq/coreutils-faq.html#Argument-list-too-long](http://www.gnu.org/software/coreutils/faq/coreutils-faq.html#Argument-list-too-long)

Something like this may work (replace "xxx" with the filename you want to delete):

```
find / -name 'xxx' -print0 | xargs -0 rm
```

---

### Post by superyounan1 on 2007-10-03
sheesh, not having too much luck today are you? it looks like bash is forking off a new process for each rm instance and not reaping children before forking some more (if i remember my systems course right). Well I don't know how to control that. Having more system memory should help, but its shooting in the dark, don't know how much memory it will take

try eph1973's perl script and dcstar's suggestion, if STILL they won't delete.........

what about doing it the manual gui way, just opening an instance of nautilus, navigate to the desktop, it should list all the files (unless that is too memory intensive too).

doing a select-all and singling out the non html files might not work, but worth a try. Otherwise you can delete them in chunks until they're all gone, increasing the chunks as you go.

If again none of these ideas work, maybe we can get you to compile a little C program and give that a shot

---

### Post by eph1973 on 2007-10-03
ok, I made a perl script, and created 271000 files.  That perl script above won't work.  Here's the solution that worked for me:

```
ls | grep html | rm xargs
```

That many files even overwhelms find, but that there should work...just do that command in the directory you want to remove all the files from.

Good luck.

---

### Post by marlinman on 2007-10-03
Sorry eph1973 - your 1st script also succumbs to the 'list too long' problem (and didn't get to try your latest idea :-(     )

superyounan1 - nautilus is out of the question I'm afraid - if I open the Desktop dir using it, and leave it for an hour even, nothing is displayed! (HDD churns tho'!) No, lady luck has certainly abandoned me today!

dcstar - I tried 

find / -name '*.html' -print0 | xargs -0 rm

and it worked!!!

!!!

!!!

Tho' a lot of messages of the form

rm: cannot remove `/etc/firefox/profile/bookmarks.html': Permission denied

appeared, so I'm guessing I should have done 'Desktop/*.html' instead of '*.html'! Hopefully nothing 'mission critical' disappeared.

Thx again to all responders...

---

### Post by Tom Mann on 2007-10-03
find / -name '*.html' -print0 | xargs -0 rm

I suspect should have been

find ~/Desktop -name '*.html' -print0 | xargs -0 rm

don't quote me on that though - you just went through your *entire filesystem!*

---

### Post by olejorgen on 2007-10-03
Ouch! Got to be careful with those nasty commands. Hope you didn't had any important html documents lying around

---

### Post by superyounan1 on 2007-10-03
at least you got them. lol, too bad you erased all your html files, i guess unless you're doing some web development it probably won't ever matter

---

### Post by marlinman on 2007-10-04
no great harm done - sadly I don't use my Ubuntu VM as often as I'd like. Plus I'm planning on installing 7.10 in a couple of weeks anyways :-)

---

### Post by superyounan1 on 2007-10-04
me too, i'm getting giddy for gutsy

---

