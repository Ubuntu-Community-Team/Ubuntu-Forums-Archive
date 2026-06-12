---
title: "Some random questions on Bash scripting"
date: 2007-07-11
forum: General Help
---

### Post by JMO707 on 2007-07-11
Hi there. I'm trying to dip myself on Bash now that I've like a month or so of winter recess ahead. I looked all over internet for a nice, but somewhat updated, guide through it.
I found [this one]("http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html"), and for his format and some content, I decided to print it and make a booklet.

Now, I'm really into this. Not that is my only thing to do (that would be a little boring), but I'm tryng to put some time everyday on it.
So, I got this little booklet by my side, plus [a list]("http://www.ss64.com/bash/") of the normal commands on any GNU/Linux distribution that, with great pleasure, I'm discovering =)

I have some assorted questions for those of you willing to share your wisdom and experience (via opinion, of course):

- I think a good way to start familiarizing with the "keyboard-way" is to try manage me all that I can throughout Bash. Always used MPD to listen music, but now I only use ncmpc (an ncurses front-end for the Shell); now started using Finch (the non-graphical way to "Pidgin", aka: IM); have the intention to use elinks everytime the browser use is not intensive; and well, running every thing I can from the prompt & using shortcuts always I can. 
Do you think this can be useful at all for my purpose, or just some kind of ankward self-punishment?

- I readed almost all the firsth chapter of the guide. Now, I need to start some script, but nano does'nt offer me too much helps on it. I've readed of vim and emacs, but vim, beeing in some way similar to vi (for what I've saw, thats, too little) result me really difficult to manage. So, my nothing-related question is: do you use any of this editors to all kind of file edition, or just for scripting?

- Now, over all what I've said: any substitute for the "Bash for Begginers" guide?, any thougth on the editors I mentioned?, any advice at all?

Thanks for your time reading this (double thanks if you answer)

---

### Post by HermanAB on 2007-07-11
Vi, joe, nano, gedit or kedit all work fine.

---

### Post by tgalati4 on 2007-07-12
The best way to learn bash is to start writing scripts.  The beginner's guide has exercises that you can try, but I find just start writing your own scripts to automate something that you want to do.

Search the forums or google for such a script and chances are somebody has already written one.  Then you can modify the script to suit your own purposes.

For instance:  Say you have a cell phone that displays a "To Do" list on the standby screen.  Say that you want to write this list on your laptop but use BlueTooth to wirelessly push the list to your phone.  A quick google search yielded the following script:

#!/bin/bash
#
# obexnote by MartinG 2004-07-14
#
# (based on some script I found posted on the web in some 
# language that I do not understand.)
# For sending notes to mobile phones using obexftp over IR or BlueTooth
#
# Feel free to improve this script - but please be kind and mail me 
# a copy: gronslet (that funny schnabel) gmail.com
#
VER=0.31
myname=`basename $0`
if [ $# -eq 0 ]; then
    echo -e "ObexNote by MartinG. Version: $VER"
    echo -e " Usage: $myname myPureTextFile.txt"
    echo -e "\tExample: $myname note1.txt"
    echo -e " If the first argument is \"-\" input is read from STDIN"
    echo -e "\tExample: echo There is no God | $myname -"
    echo -e "\tExample: cat bible.txt | $myname -"
    exit 1
fi;

file=$1
name=`basename $1 .txt`

# Safety first... Use a random number in temporary files if for some
# odd reason multiple copies run at the same time...
R=$RANDOM
if [ $1 == "-" ]; then
    tee /tmp/tmp-irnote$R >/dev/null
    file=/tmp/tmp-irnote$R
    name=""
fi;

notetmpfile=/tmp/NOTE-$R-
vnttmpfile=/tmp/note-$R.vnt
## A note can have max 500 letters, therefore splitting to 420
## leaving room for headers
split -b 420 $file $notetmpfile
NUMBER="1"
for j in $(ls $notetmpfile*) ; do
    VAR="$NUMBER $name" 
    echo "BEGIN:VNOTE " > $vnttmpfile
    echo "VERSION:1.1 " >> $vnttmpfile
    echo "BODY: $(for i in $(cat $j ) ; do VAR="$VAR $i"; done; echo $VAR) " >> $vnttmpfile
    echo "DCREATED:$(date +%Y%m%dT%H%M00 ) " >> $vnttmpfile
    echo "LAST-MODIFIED:$(date +%Y%m%dT%H%M00 ) " >> $vnttmpfile
    echo "CLASS:PUBLIC " >> $vnttmpfile
    echo "X-IRMC-LUID:000001000000 " >> $vnttmpfile
    echo "END:VNOTE " >> $vnttmpfile
# Archive note:
    echo Archiving note to $HOME/notes/$name$NUMBER.vnt
    cp $vnttmpfile $HOME/notes/$name$NUMBER.vnt
# This is where the note is being sent over IR (Or BlueTooth or whatever)...
    echo Sending note...
#btctl put 1 /tmp/nota.vnt
    obexftp -p $vnttmpfile
    echo "Message part $NUMBER"
    echo "===================================================="
    echo "===================================================="
    cat $j
    echo ""
    echo "===================================================="
    echo " Press Accept Note on mobile device, "
    echo " then press Enter to transfer next part - if any. " 
    echo "===================================================="
    read NADA
    let NUMBER=$NUMBER+1

    rm $vnttmpfile
done

echo Cleaning up...
rm -f $notetmpfile*
# Remove pipe temp file:
rm -f /tmp/tmp-irnote$R
echo done.

-------------------------------------

That's how it's done. 

Using the command line exclusively is good for really old hardware--the kind that can't run X Windows.  I'm not sure how helpful it is if you have more modern hardware--since the graphical environment adds perhaps only 10% overhead.

Just come up with a really neat thing that you want your computer to do and there is a bash script already written just waiting for tweaking by you.

---

### Post by Nythain on 2007-07-12
i think its great to familiarize ones self with the cli and bash in general... i've found better apps for the cli than a lot of gui equivalents or front ends... life without rtorrent would suck... i suggest centericq for im, but i havent tried the one you use... im now more familiar with midnight commander than i was with konqueror and i find myself typing more in eterm than doing anything else

then there's the fact that once one is familiar with bash scripting life becomes even easier... automating some of the more daunting tasks is always a bonus... keep up the learnin mate :)

side note, i use nano for all my cli text editing... though i do keep leafpad around for those times when i prefer a graphical text editor

---

### Post by spupy on 2007-09-05
Syntax highlighting for bash scripts is not enabled by default in nano. But its nice. I write my scripts in nano because i never brought myself to learn vi/emacs hehe. I like leafpad because its DAMN FAST! But still nano is easy and has highlighting.
Some tipps from me:
- The man pages are your best friend. After you write couple of scripts, you will memorize the man pages of the most common commands (like grep...) ;)
- Make a dir for your scripts and add this dir to your PATH, so you can reach the scripts from everywhere.
- Learn regular expresions. [http://xkcd.com/208/]("http://xkcd.com/208/"). They are a really powerfull tool!
- grep, piping, output redirection - commonly used (at least i do :O )
- _zenity_ is a really nice program, i use it alot in my scripts.

---

