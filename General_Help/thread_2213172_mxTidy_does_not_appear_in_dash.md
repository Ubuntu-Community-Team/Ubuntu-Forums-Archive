---
title: "mxTidy does not appear in dash"
date: 2014-03-25
forum: General Help
---

### Post by ortermagic on 2014-03-25
Hello, I have just installed mxTidy (an html syntax checker) Does anyone know why it does not show up in the dash or as far as I can see anywhere else. It is listed as installed in the software center and shows up in synaptic but I can't find it, does it auto attach to the text editor by any chance?

---

### Post by Lars Noodén on 2014-03-25
I can't find mxTidy in the repository, just regular tidy.  If you mean the latter, it is a text-based program that you need to run via the shell or as part of a launched script.

---

### Post by ortermagic on 2014-03-25
Hi, could you please show me how to run tidy (that's what I've got ) via the shell? when I launch a script it's not anywhere obvious. Sourceforge calls it mxTidy I think.
I ran   tidy -config but nothing happened

---

### Post by Lars Noodén on 2014-03-25
[tidy](http://manpages.ubuntu.com/manpages/trusty/en/man1/tidy.1.html) has about a million options so it is a good idea to look at the manual page to see what it can do.  However, 99.9% of the time I use it one of three ways.  

Sometimes I convert a file in-place to XHTML.

```

tidy -m -asxml somefile.html

```

and mostly I check XHTML files in-place for errors

```

tidy -m -xml somefile.html

```

and sometimes I check the file without modifying it.

```

tidy -xml somefile.html

```

That's the basic use, but there are many, many options for different occasions.  It's a great program.

---

### Post by ortermagic on 2014-03-25
Thank you I will try those hints

---

### Post by Lars Noodén on 2014-03-25
It may help to make back up copies of the files, especially in the beginning while you are learning how it works.

---

### Post by ortermagic on 2014-03-25
I am getting this from tool output

> Running tool: Build

No Makefile found!

Done.


and this from Python Console 

> You can access the main window through 'window' :
<Window object at 0x7fae8577b4c8 (GeditWindow at 0x151fbb0)>
>>> 


Found at the bottom of the gedit text editor screen not sure what it means tho

---

### Post by Lars Noodén on 2014-03-25
How are you running it and do you have the version from the repository? I usually open a termiinal (ctrl-alt-t) to do so.

---

### Post by ortermagic on 2014-03-25
I got the pointer to the programme from the source forge site but installed through the software centre, tried to call it up using the terminal but got null.

The output of gedit external tools are as follows

> #!/bin/sh

EHOME=`echo $HOME | sed "s/#/\#/"`
DIR=$GEDIT_CURRENT_DOCUMENT_DIR
while test "$DIR" != "/"; do
    for m in GNUmakefile makefile Makefile; do
        if [ -f "${DIR}/${m}" ]; then
            echo "Using ${m} from ${DIR}" | sed "s#$EHOME#~#" > /dev/stderr
            make -C "${DIR}"
            exit
        fi
    done
    DIR=`dirname "${DIR}"`
done
echo "No Makefile found!" > /dev/stderr


[COLOR=#a52a2a]*this from open terminal here*[/COLOR]


#!/bin/sh

#TODO: use "gconftool-2 -g /desktop/gnome/applications/terminal/exec"
gnome-terminal --working-directory=$GEDIT_CURRENT_DOCUMENT_DIR &

[COLOR=#a52a2a]*this from remove trailing spaces*[/COLOR]

#!/bin/sh

sed 's/[[:blank:]]*$//'

[COLOR=#a52a2a]*this from run command*[/COLOR]


#!/bin/sh

#TODO: use "gconftool-2 -g /desktop/gnome/applications/terminal/exec"
eval $(zenity --entry --title="Run Command - gedit" --text="Command to run:")




I must admit I'm a little out of my depth at the moment

---

### Post by Lars Noodén on 2014-03-25
I'm not sure about the sourceforge material, the one from the repository should work just fine in the terminal with the methods I described above.  What are you typing in the terminal exactly?  How is gedit involved?

---

### Post by Lars Noodén on 2014-03-25
Also, did you get tidy via synaptic or the Software Center?  They both do the same thing, but it helps to know a little background.

---

### Post by ortermagic on 2014-03-25
I ran the following

```
ortermagic@ortermagic:~$ tidy -config


```

Well I normally use gedit as my text editor. My main issue at the moment has been with trailing spaces,which I had hoped to eliminate with tidy.

I used the software center to install

---

### Post by Lars Noodén on 2014-03-25
Try one of the ways I mentioned in #4 above.  The -config looks for configuration options in a file and that is a little advanced for right now so it is not needed.  

About the trailing spaces in gedit, try

Search -> Replace -> Match as regular expression -> Search for **\s$**

That should get rid of trailing [white space](http://www.regular-expressions.info/quickstart.html) from the end of the lines.

---

### Post by ortermagic on 2014-03-25
Thank you so much for the white space tip Lars, that has helped me with my main problem, I will now try some of the suggestions you posted at #4

---

### Post by ortermagic on 2014-03-25
I see what you mean re backing up until I am a bit more competent with tidy, heh heh!

---

