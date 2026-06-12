---
title: "bash treatment of tilde character ~"
date: 2008-05-07
forum: General Help
---

### Post by oaul on 2008-05-07
Hello -
We all (hopefully) know about bash's interpretation of the ~ character.  Let's use cd command as an example
```

$ cd ~
```
does exactly what you would expect. 


But what about passing tilde to cd when it is the output of some program?
```

$ cd `echo \~`
bash: cd: ~: No such file or directory
```


I tried the following variants, and none of them work:
```

$ cd "`echo \~`"
$ cd $(echo \~)
```
These work in csh (except that last one - which is exclusively bash... i think)

You may be a smartass and say "The answer is: Who gives a ****?".  But this would actually be really useful because the directory stack shows all directories in terms of ~ when applicable.
So you could do something like cd $(dirs +1), in a directory stack that looks like:
 0  /etc
 1  ~

Anyone know how to pass STDOUT tildes to other programs so it behaves like passing the home directory?

---

### Post by Monicker on 2008-05-07
I am not sure why you are you using "\~" in your example of combining it with the cd command. The \ tells it to interpret ~ literally.

This works fine for putting me in my home directory.
```
cd "`echo ~`"
```


What are you running that actually outputs "\~"  ?

---

### Post by bingoUV on 2008-05-07
> **oaul said:**
> Hello -
We all (hopefully) know about bash's interpretation of the ~ character.  Let's use cd command as an example
```

$ cd ~
```does exactly what you would expect. 


But what about passing tilde to cd when it is the output of some program?
```

$ cd `echo \~`
bash: cd: ~: No such file or directory
```I tried the following variants, and none of them work:
```

$ cd &quot;`echo \~`&quot;
$ cd $(echo \~)
```These work in csh (except that last one - which is exclusively bash... i think)

You may be a smartass and say &quot;The answer is: Who gives a ****?&quot;.  But this would actually be really useful because the directory stack shows all directories in terms of ~ when applicable.
So you could do something like cd $(dirs +1), in a directory stack that looks like:
 0  /etc
 1  ~

Anyone know how to pass STDOUT tildes to other programs so it behaves like passing the home directory?

 For me, csh 6.15.00 (Astron) 2007-03-03 (i386-intel-linux) options wide,nls,dl,al,kan,sm,rh,color,filec, neither of the examples work, that you say work in csh. 

Only raw appearances of ~ are substituted by the home directory. For example, would you expect  ```
 cd  `echo -n $``echo -n H``echo -n O``echo -n M``echo -n E` 
``` to behave identically as  ```
 cd $HOME 
``` ?In shells, like programming languages, assembling a variable name from raw characters or outputs from other commands does not result in evaluation of those variables. To cause evaluation, you have to call evaluator again. eval does that job in bash. All of the following work ```
 eval cd &quot;`echo \~`&quot; 

eval cd $(echo \~) 

eval cd `echo \~` 
```

---

### Post by oaul on 2008-05-07
Remember that 
$echo ~
Does NOT send a tilde to STDOUT.  It sends your home directory to standard out.  Yeah it will work fine for that case.

The key here is output that is actually a tilde - not backslash tilde and not your home dir.

Do these commands to get a better picture of what I'm saying:
```

cd ~
pushd /etc
dirs -v; #show the directory stack 
dirs +1; #shows the home director is inside the stack
cd `dirs +1` ; #doesn't work

```

Hopefully that makes more sense.

---

### Post by oaul on 2008-05-07
Ahh.. eval is the key.

I'm too used to Tcl as I was doing cd `eval...`. 

It's interesting though that you can't get 
$ cd `echo \~` 
to work in csh.  I'm on Solaris though...

EDIT:
I should have read your post more closely.  Also I should have tried out that double-quoted example I showed you - it does NOT work in csh.  My bad.
END EDIT

Anyways, I don't really care.  Thanks for the help - problem solved

---

