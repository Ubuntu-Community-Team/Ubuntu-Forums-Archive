---
title: "tab complete not functioning at terminal"
date: 2006-08-04
forum: General Help
---

### Post by shoagun on 2006-08-04
Tab completion is not working properly for me at the terminal(you can imagine how annoying this is).  The problem is seems pretty strange.  Here is an example.  (Don't worry about what the commands actually do, just whether pressing [Tab] completes the file name.)  Say I am in some directory with only the following files:

script.pl   file1.txt   file2.txt

Typing "cp file1[Tab] file2[Tab]" works (ie pressing [Tab] completes the file names)

Typing "perl s[Tab] file1[Tab]" doesn't work.  Pressing [Tab] DOES complete "script.pl" (s[Tab] -> script.pl) but DOES NOT complete "file1.txt".

This was not happening yesterday.  I have no idea what could have caused the problem.  Any clues???

---

### Post by jayemef on 2006-08-04
What is the exact behavior? Assuming the only contents of your working directory are these three files, what *should* happen is that completion will fill up to **perl script1.pl file**. This is where the ambiguity starts, in that you have more than 1 option. From here, you should either be able to hit tab twice to display all possible completions (file1.txt file2.txt), or hit 1 or 2 and press tab again to finish off the file.

---

### Post by shoagun on 2006-08-04
I realized the only thing I've done since yesterday (when Tab completion was woking) was intall the automatic updates for Ubuntu.  I'm using 6.06 LTS.  To test to see if the updates might be involved with the problem, I SSHed onto another Ubuntu machine and a RedHat machine.  Tab completion is working fine on the RedHat machine but is not working on the other Ubuntu machine.

---

### Post by shoagun on 2006-08-04
jayemef,
You're right, that's what *should* happen.  However, that is not what happens.  Hitting tab does nothing.  Hitting tab multiple times does nothing.  (Actually, if you look carefully at my example, you'll see that I specifically typed in "file1" before hitting tab, so that hitting tab once should complete the file name.)  

Again, [Tab] does complete the name of the perl script, but it does not complete the name of any file being given to the perl script as an argument.

---

### Post by vdemeester on 2006-08-06
> **shoagun said:**
> Again, [Tab] does complete the name of the perl script, but it does not complete the name of any file being given to the perl script as an argument.

I have the same behavior with my ubuntu. I think it's because two
way of completion. Long time ago (6 months) i installed Gentoo in my desktop, by defaut no tab-completion was installed. I look at the [gentoo wiki]("http://gentoo-wiki.com/TIP_TAB-completion") and my rab-completion worked well for file, command and argument.

I didn't find a way to reproduce it in Ubuntu, but i didn't search..

---

### Post by vdemeester on 2006-08-06
If you look at /etc/bash_completion.d/, you could see the script to have a "complete" bash_completion, for example with svn..
I think more of these script are available on ubuntu rep. but.. :/

---

### Post by shoagun on 2006-08-06
i have three files in /etc/bash_completion.d/
They are:

debconf   ooffice.sh   pon

I'm assuming pon is the relevant one.  Here is what pon shows:

# Debian GNU/Linux pon/poff(1) completion
# Copyright 2002 Baruch Even <baruch@debian.org>
# License: GNU GPL v2 or later

have pon &&
_pon()
{
        local cur conns

        [ -r /etc/ppp/peers/ ] || return 0

        COMPREPLY=()
        cur=${COMP_WORDS[COMP_CWORD]}
        conns=$(ls --color=none /etc/ppp/peers | egrep -v '(\.bak|~)$')

        if [ $COMP_CWORD -eq 1 ]; then
                COMPREPLY=( $(compgen -o filenames -W "$conns" $cur) )
        fi

        return 0
}
[ "$have" ] && complete -F _pon pon

have poff &&
_poff()
{
        local prev cur conns

        [ -r /etc/ppp/peers/ ] || return 0

        COMPREPLY=()
        prev=${COMP_WORDS[COMP_CWORD-1]}
        cur=${COMP_WORDS[COMP_CWORD]}
        conns=$(ls --color=none /etc/ppp/peers | egrep -v '(\.bak|~)$')

        if [[ "$cur" == -* ]]; then
                COMPREPLY=( $(compgen -W '-r -d -c -a -h -v' -- $cur) )
                return 0
        fi

        # first parameter on line or first since an option?
        if [ $COMP_CWORD -eq 1 ] && [[ "$cur" != -* ]] || \
          [[ "$prev" == -* ]]; then
                COMPREPLY=( $(compgen -o filenames -W "$conns" $cur) )
        fi

        return 0
}
[ "$have" ] && complete -F _poff poff

# vim:ft=sh:

---

### Post by vdemeester on 2006-08-06
Hum, i dont have more files there (7), with inkscape, ..

I don't know what is this file (i have too), but there is "/etc/ppp/peers".. ppp is a way to connect on internet isn't it ? So why it's there.. hum..

---

### Post by entropic_existence on 2007-09-05
Well this is a year old thread so it may be irrelevant but I will post the solution I used here in case anyone reads this:

You need to edit the /etc/bash_completion file. Find the following section (in _perl)

    # handle case where first parameter is not a dash option
    if [ $COMP_CWORD -eq 1 ] && [[ "$cur" != -* ]]; then

Change the if line to read: 

if [[ "$cur" != -* ]]; then


Start a new shell terminal and tab-complete away!

---

### Post by flyingstar16 on 2008-03-04
Other working solution (tried on Hardy Heron alpha5)
From Synaptic try to install (or re-install) the "bash-completion" package :)
(Hope this is as simple as KISS rule says xD):lolflag:

---

### Post by AbtZ on 2008-03-06
That last solution worked fine for me. Thanks!

---

### Post by yoasif on 2008-04-21
I installed bash-completion, but in my fresh install of hardy, it doesn't function in the same way as the bash in ubuntu... 

i cannot for example do: sudo apti<tab> and have it auto complete to aptitude... any idea how "ubuntu" manages this feat?

---

