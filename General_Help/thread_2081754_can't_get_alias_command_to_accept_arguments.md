---
title: "can't get alias command to accept arguments"
date: 2012-11-07
forum: General Help
---

### Post by droidChris on 2012-11-07
Hi there
Im trying to alias two commands (cd and ls) so that i can cd into a target directory and print its content:

alias cdl="cd;ls"
or
alias cdl="cd $1; ls"

It kind of worked!! I got the content of the selected directory printed on the screen but I ended up in my home directory.

Any idea whats wrong?

Thanks for your time.
Chris.

---

### Post by hal8000 on 2012-11-07
> **droidChris said:**
> Hi there
Im trying to alias two commands (cd and ls) so that i can cd into a target directory and print its content:

alias cdl="cd;ls"
or
alias cdl="cd $1; ls"

It kind of worked!! I got the content of the selected directory printed on the screen but I ended up in my home directory.

Any idea whats wrong?

Thanks for your time.
Chris.

cd  (on its own) changes you into your home directory, its the same as typing cd ~
The alias command is interpreting the cd to change you into home directory.
I tried placing () or '' around it but cant get it working yet, I'm sure someone will post a solution shortly

---

### Post by steeldriver on 2012-11-07
I think you need a *shell function* rather than an alias - see

[http://ubuntuforums.org/showthread.php?t=2011495](http://ubuntuforums.org/showthread.php?t=2011495)

---

### Post by sienile on 2012-11-07
You have the wrong placeholder for the argument.
```
alias cdl="cd \!*; ls"
```
That should work.

You might also want to have it go back to the directory you started in.
```
alias cdl="cd \!*; ls; cd .."
```

---

### Post by drmrgd on 2012-11-07
> **sienile said:**
> You have the wrong placeholder for the argument.
```
alias cdl="cd \!*; ls"
```
That should work.

You might also want to have it go back to the directory you started in.
```
alias cdl="cd \!*; ls; cd .."
```

I don't think that works quite right.  Also, the return command you posted isn't correct.  You would want 'cd -' there not 'cd ..' , which just goes up one directory level.

Aliases aren't good things for taking arguments.  I think as others have said, it'd be best to put a shell argument in your .bashrc, which will work just as well, and give you much more flexibility.

Try something like this (a bit crude, but should work):

```
function cdls () {
        if [ ! -d "$1" ]; then
                printf "The directory: %s does not exist\n" "$1"
        else
                ( cd "$1" && ls )
        fi
}
```

---

### Post by droidChris on 2012-11-07
Hi guys
I put the shell script into bash.bashrc but the result is the same. I get the listing but dont go anywhere.
Thats weird:)
Gonna play around with tje script and will let you know.

Cheers.
Chris.

---

### Post by Slim Odds on 2012-11-07
> **droidChris said:**
> Hi guys
I put the shell script into bash.bashrc but the result is the same. I get the listing but dont go anywhere.
Thats weird:)
Gonna play around with tje script and will let you know.

Cheers.
Chris.
I would highly recommend pushd and popd

---

