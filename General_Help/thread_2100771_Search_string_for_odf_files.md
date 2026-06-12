---
title: "Search string for odf files"
date: 2013-01-02
forum: General Help
---

### Post by dreamquartz on 2013-01-02
HAPPY NEW YEAR!!!!!!!!!!!!!!!!!

I am still trying to solve the search a text-string issue within odf-files, and came across the following:

[I]function odfgrep(){
FILE=$1
shift
EXT=`echo ${FILE##*.}`
case $EXT in
       odt|ods|odp)
      unzip -p "$FILE" content.xml | tidy -q -xml 2> /dev/null | grep "$@" ;;
       txt|t2t)
      grep  "$@" "$FILE" ;;
       *) echo "Sorry, I don't know what to do with $FILE"
       ;;
esac
}[/I]
as listed on: [http://www.techrepublic.com/blog/opensource/how-to-search-for-text-inside-many-opendocument-files/3696](http://www.techrepublic.com/blog/opensource/how-to-search-for-text-inside-many-opendocument-files/3696)

It appears that the function is an easy one, but it does not work on my computer.
When in Terminal, I enter: odfgrep "string" (without the quotation marks) and my system returns: *No command 'odfgrep' found*.

I added the function to .bashrc, saved it, re-booted, but NOTHING:confused::cry:.

Any idea anyone?

DREAM

---

### Post by sudodus on 2013-01-02
Such a function works within a shell-script. It should be called by the script. Put the script it into a file, make it executable and give it a suitable name. Then it should be possible to run from a terminal window.

Good luck :-)

---

### Post by TheFu on 2013-01-02
Load **recoll** search tool instead.  It is like a google search, but only where you specify on your local network.

If you insist on using a bash function, review the **Advanced Bash Scripting Guide** for help. google will find that easily.

Or you can wait for someone with more specific experience than I have to answer. ;)

---

### Post by Vaphell on 2013-01-02
create bin dir in your home, it's added automatically to $PATH if it exists. Scripts located there can be run from any location.
Create script file (odfgrep i assume?), in the script put the body of that function
You could add that function to one of the shell config files so it's loaded every time but i don't see the point.

btw, replace
```
EXT=`echo ${FILE##*.}`
```
with
```
EXT=${FILE##*.}
```
embedded echo to extract extension is not necessary

and don't use all-caps names, you will override some all-caps shell variable by accident and you won't know what happened.

---

### Post by Cheesehead on 2013-01-02
You listed a function...but nothing calls that function.
You also didn't say that you made it executable.
I don't understand why you added it to .bashrc. Unless you had a good reason, you should probably remove it.

There are some really great tools for searching and manipulating OO/LO documents, spreadsheets, drawings, and databases using the published API and Python bindings. Is there something specific you are looking for?

---

### Post by sudodus on 2013-01-03
> **TheFu said:**
> Load **recoll** search tool instead.  It is like a google search, but only where you specify on your local network.

If you insist on using a bash function, review the **Advanced Bash Scripting Guide** for help. google will find that easily.

Or you can wait for someone with more specific experience than I have to answer. ;)
+1 for recoll :-)

---

### Post by TheFu on 2013-01-03
> **Cheesehead said:**
> You listed a function...but nothing calls that function.
I don't understand why you added it to .bashrc. 

Putting functions into your .dotfiles means you can call them from scripts or the shell later. This has been a common technique the last 30+ yrs on UNIX systems.

---

### Post by conradin on 2013-01-03
>This
[http://ubuntuforums.org/showthread.php?t=899179&page=1](http://ubuntuforums.org/showthread.php?t=899179&page=1)

---

### Post by Cheesehead on 2013-01-04
> **TheFu said:**
> Putting functions into your .dotfiles means you can call them from scripts or the shell later.

Ah, thanks!
I had not run across that.
Now I understand it.

My experience is from the other end of the question - creating valid .odt files from data.

---

### Post by dreamquartz on 2013-01-05
> **sudodus said:**
> +1 for recoll :-)
Tried it, does not with my 12.04

Dream

---

### Post by sudodus on 2013-01-05
> **dreamquartz said:**
> Tried it, does not with my 12.04

Dream
It works in my Ubuntu 12.04. I installed it from the repos

Version: Recoll 1.16.2 + Xapian 1.2.8

```
sudo apt-get install recoll
```

---

### Post by dreamquartz on 2013-01-05
> **sudodus said:**
> It works in my Ubuntu 12.04. I installed it from the repos

Version: Recoll 1.16.2 + Xapian 1.2.8

```
sudo apt-get install recoll
```

It installed, indexed, but does not find strings in odf-files, which is my original problem.
Would like to be able to search strings inside odf-files.

Dream

---

### Post by sudodus on 2013-01-05
> **dreamquartz said:**
> It installed, indexed, but does not find strings in odf-files, which is my original problem.
Would like to be able to search strings inside odf-files.

Dream

In the manual I found
> As of Recoll release 1.14, a number of XML-based formats that were handled by ad hoc filter code now use the xsltproc command, which usually comes with libxslt. These are: abiword, fb2 (ebooks), kword, openoffice, svg.

Now for the list:

Openoffice files need unzip and xsltproc.

I have recoll version 1.16, unzip and xsltproc, and tested with an odt file, and you are right, recoll does not work.

So until that is solved, we need to go back to a script.

---

### Post by TheFu on 2013-01-05
> **sudodus said:**
> In the manual I found
I have recoll version 1.16, unzip and xsltproc, and tested with an odt file, and you are right, recoll does not work.
So until that is solved, we need to go back to a script.

Color me disappointed with Recoll.  I thought it used to work, honest!  OTOH, where I work we use Alfresco for document storage which does handle full-text searching, but that would be overkill for a single person.

The script seems like the best way ... or use an indexer like swish-e ... as my buddy JoshR explains here: [http://www.linuxjournal.com/article/6652](http://www.linuxjournal.com/article/6652) or directly in PDF here: [http://www.joshr.com/src/docs/HowToIndexAnything.pdf](http://www.joshr.com/src/docs/HowToIndexAnything.pdf)

---

### Post by sudodus on 2013-01-05
> **conradin said:**
> >This
[http://ubuntuforums.org/showthread.php?t=899179&page=1](http://ubuntuforums.org/showthread.php?t=899179&page=1)
Thanks a lot!

I could not refrain from tweaking the scripts shown in that thread. I wanted to make a script that is easy to understand, at least for me ;-)

This one does the job for odt, ods and odp files (also if the file-names contain spaces).

```
#!/bin/bash

if [ $# -ne 2 ]; then
        echo "Usage: $0 searchpath searchterm"
        echo "finds text string 'searchterm' in odt, ods or odp files"
        exit 1
fi

find "$1" -name \*.od[tsp]| while read file
do
        unzip -ca "$file" content.xml | grep -qli "$2"
        if [ $? -eq 0 ]; then
                echo "Found '$2' in: " $file
        fi
done
```

*Edit*: [FONT="Courier New"][SIZE="3"]find [COLOR="Red"]"[/COLOR]$1[COLOR="red"]"[/COLOR] -name [COLOR="RoyalBlue"]**\**[/COLOR]*.od[tsp]| while read file[/SIZE][/FONT]
to manage also a searchpath with spaces: [COLOR="red"]"[/COLOR] and 'every' searchpath (e.g. current directory) : [COLOR="RoyalBlue"]**\**[/COLOR]

---

### Post by dreamquartz on 2013-01-06
> **sudodus said:**
> Thanks a lot!

I could not refrain from tweaking the scripts shown in that thread. I wanted to make a script that is easy to understand, at least for me ;-)

This one does the job for odt, ods and odp files (also if the file-names contain spaces).

```
#!/bin/bash

if [ $# -ne 2 ]; then
        echo &quot;Usage: $0 searchpath searchterm&quot;
        echo &quot;finds text string 'searchterm' in odt, ods or odp files&quot;
        exit 1
fi

find $1 -name *.od[tsp]| while read file
do
        unzip -ca &quot;$file&quot; content.xml | grep -qli &quot;$2&quot;
        if [ $? -eq 0 ]; then
                echo &quot;Found '$2' in: &quot; $file
        fi
done
```

 K, does it work?
If so, I have no idea how to run a script. It should be easy to run.

Dream

---

### Post by sudodus on 2013-01-06
> **dreamquartz said:**
> K, does it work?
If so, I have no idea how to run a script. It should be easy to run.

Dream
You open a terminal windows with the hotkey combination

***ctrl + alt + t***

all three keys at the same time. In the terminal, type (or paste)

```
mkdir ~/bin
```
```
cd ~/bin
```
Finish each line with the ***ENTER*** key to launch the command.

Now start an editor and create a script file. You seem to run [vanilla] Ubuntu. Then you have gedit. So start it with the following command:
```
gedit searchodf
```
***Cut and paste the whole content of the code-box in post #15 into the window of gedit***

(starting with #!/bin/bash, ending with done). Save it!

Now you should have a file with the name searchodf in the directory ~/bin (/home/your-user-name/bin). Give it execute permissions
```
chmod ugo+x searchodf
```

Reboot, and you should have ~/bin in your $PATH variable and your script will be easy to run :-) from a terminal window.

***ctrl + alt + t***

```
searchodf
``` prints the help text
```
Usage: /home/your-user-name/bin/searchodf searchpath searchterm
```
```
searchodf ~/Documents linux
``` prints a line for each odf file in your ***Documents*** folder (~/Documents), where it finds the text 'linux'
```
searchodf ~/Documents 'Hello World'
``` prints a line for each odf file, where it finds the text 'Hello World'

---

### Post by medoc on 2013-01-06
> **sudodus said:**
> In the manual I found


I have recoll version 1.16, unzip and xsltproc, and tested with an odt file, and you are right, recoll does not work.

So until that is solved, we need to go back to a script.

Hello,

I am the Recoll developer. Recoll does search odt files in general. Hundreds, possibly thousands, of people use this. 

Reporting a bug would be useful, maybe you are doing something wrong, or maybe you can get me to fix a problem.

If you are interested in helping, please create an issue on the bitbucket tracker: [https://bitbucket.org/medoc/recoll/issues/new](https://bitbucket.org/medoc/recoll/issues/new)

And we'll take it from there. 

Cheers,

jf

---

### Post by sudodus on 2013-01-06
> **medoc said:**
> Hello,

I am the Recoll developer. Recoll does search odt files in general. Hundreds, possibly thousands, of people use this. 

Reporting a bug would be useful, maybe you are doing something wrong, or maybe you can get me to fix a problem.

If you are interested in helping, please create an issue on the bitbucket tracker: [https://bitbucket.org/medoc/recoll/issues/new](https://bitbucket.org/medoc/recoll/issues/new)

And we'll take it from there. 

Cheers,

jf
Done: issue #124, 'I can't find strings in odf files'

I'd be glad to learn how to use it or to help, if I can.

---

### Post by sudodus on 2013-01-07
Well, what should I say? Maybe I should blush :oops: because I simply forgot to reindex my computer. After reindexing, Recoll found the simple test file using a string in its content, in this case: 'This text is (was originally) in the test file test.odt'. And my next step was to check with other odf files, and they work too.

So I am sorry to have bothered medoc with this unnecessary issue.
Summary: Recoll does what it is supposed to do, and it does it well :-)
--
Tip to the OP and other new users: Use the pull-down menu

***File -- Update index***

to create or update an index file for all the files in the computer. This may take some minutes, if you have many files. After that Recoll will work very quickly and efficiently.

---

### Post by TheFu on 2013-01-07
Recoll is an amazing search tool.  It is like having google on your PC and network, but not having to share data with any 3rd party.

**Recoll completely rocks.**

---

