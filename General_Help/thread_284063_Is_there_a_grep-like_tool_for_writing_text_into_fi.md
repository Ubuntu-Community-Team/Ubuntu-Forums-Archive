---
title: "Is there a grep-like tool for writing text into files?"
date: 2006-10-25
forum: General Help
---

### Post by kvonb on 2006-10-25
I'm working on a script to simplify the ATI driver install and I know how to use grep to find text in a file, but I would like to be able to search for a string in a file, then add some new lines into the file, eg:

search file for string "this is line 20"
then add "this is line 21" "<CR>" "this is line 22" "<CR>" etc'

Any ideas?

Thanks, Kev :)

---

### Post by Alex_Perry on 2006-10-25
try [this]("http://www.linuxsa.org.au/tips/io-redirection.html") site.

---

### Post by kvonb on 2006-10-25
Not quite what I needed Alex, but thanks for the reply.

Maybe I'm not being very clear, what I need to do is find a string in a given file, then append several lines after that string, the insertion point will have text after it, hence the standard ">>" append will not work.

Or to put it another way, insert some lines into the middle of a text file from a shell script.

I'm not an expert at script writing either :D

Regards,  KEv :)

---

### Post by po0f on 2006-10-25
kvonb,

I don't know how to use it, but you will want to look at [sed](http://www.grymoire.com/Unix/Sed.html).

---

### Post by matthewstory on 2006-10-25
what you might want to do is to write a bash script that uses an exec loop, so that you read the file line by line in a loop, then grep the line you grabbed, if grep, then add your lines, else then just echo:

#!/bin/bash
grepvar=test
exec < /path/to/file
while read line
do
if echo $line | grep $grepvar
then
echo $line 1>> /path/to/newfile
echo "More Lines" 1>> /path/to/newfile
echo "More Lines" 1>> /path/to/newfile
else
echo $line 1>> /path/to/newfile
fi
done

---

### Post by kvonb on 2006-10-25
YES, sed is the bomb!!!!

Thanks po0f.

Now for some editing ;)

---

### Post by Ramses de Norre on 2006-10-25
```
sudo sed -i -e 's/ati/fglrx/g' /etc/X11/xorg.conf
```

---

### Post by kvonb on 2006-10-25
I'm trying to figure out the syntax, can you help me a little?

The command you gave me Ramses is excellent, but instead of replacing the text, I'd like to search for the string (as in your example) "ati", and insert after it "fglrx".

sudo sed -i -e 's/ati/fglrx/g' /etc/X11/xorg.conf
                ^           ^
                |           |
Can you tell me what these 2 commands do?

Thanks, KEv :)

---

### Post by po0f on 2006-10-25
kvonb,

The spacing on your arrows there got messed up.  Are you referring to the sed command preceded by sudo?  This runs the command as the root user, meaning you can edit configuration files that normal users shouldn't be able to write to.

Here's a break down:
[LIST]
[*]sudo: run the command as the root user.
[*]sed: the command (duh!)
[*]-i: from the [man-page](http://unixhelp.ed.ac.uk/CGI/man-cgi?sed), edit a file in place.
[*]-e: execute the following script.
[*]'s/ati/fglrx/g': replaces **all** occurences of ati with fglrx. If it had been just 's/ati/fglrx/', only the first occurence would have been replaced.
[*]/etc/X11/xorg.conf: the file to execute the script on.
[/LIST]

---

### Post by kvonb on 2006-10-25
Sorry, I meant the s and the g, I tried to put those arrows underneath the s and g but unfortunately it didn't turn out right!  And I had to run off and do something else.

But I get it now, thanks :D

---

### Post by po0f on 2006-10-25
kvonb,

s means switch, s/a/A/ switches a lower-case "a" with an upper-case "A".  The g at the end means all occurences.  Given the file:
```
I love my foo.
Do you love foos too?
```
s/foo/bar/g would output:
```
I love my bar.
Do you love bars too?
```
s/foo/bar/2 would have replaced the second occurence of foo with bar, ie:
```
I love my foo.
Do you love bars too?
```

Hope this helps.

---

### Post by kvonb on 2006-10-25
I LOVE LINUX!!!!

These small command line tools are the best, makes me feel like I'm flying a jet fighter!

OK, I've settled down a bit now, this is what I did:

sudo sed -i -e '/OpenGLOverlay/ a\        Option      "UseInternalAGPGART" "no"' /etc/X11/xorg.conf

And it worked perfectly.

Now just to be a little more annoying, I have another boring question:

Can I use sed to abort the edit if it finds the string "UseInternalAGPGART" and skip to the next search string?

I know I should read through the manual, but it takes so long to find the small thing I need.

Thanks, Kev :)

---

### Post by kvonb on 2006-10-25
Here is the pseudo code of what I want to do:


if ! exists "string1"
  write "string1"
endif
if ! exists "string2"
  write "string2"
endif
if ! exists "string3"
  write "string3"
endif
end

---

### Post by po0f on 2006-10-25
kvonb,

Maybe something like the following? (untested):
```
$ grep "UseInternalAGPGART" /etc/X11/xorg.conf || sed_command
```

grep returns 0 on a match, so the other command should be executed.  Like I said, it's untested, back up xorg.conf before doing it.  ;)

---

