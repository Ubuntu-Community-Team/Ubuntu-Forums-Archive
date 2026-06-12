---
title: "how do i execute any perl pl script from any directory?"
date: 2007-01-06
forum: General Help
---

### Post by John_a12357 on 2007-01-06
Hi, I have spent the better part of the day searching for what modifications I need to make to whatever file so I can execute any perl program from any folder - or just so that I can execute a perl (pl) script without needing to type 'perl my_script.pl' every time. What I really need is the ability to use cron and execute various scripts at various times. So far 10 hours of wasted time - any help is most appreciated - thanks

---

### Post by tomchuk on 2007-01-06
Well, you can do a few things...
1. Set the executable bit on the script - `chmod +x script.pl`
Now you'll be able to run it as `/path/to/script.pl`
2. Place your script(s) in somewhere in your $PATH. I put all my custom scripts in /usr/local/bin.
Now you can run it as `script.pl`

---

### Post by koenn on 2007-01-06
apart from the things in post 2, you're script would have to start with something like

#!/path/to/perl

---

### Post by John_a12357 on 2007-01-06
Thank you for the fast reply. My steps:

1. cd /usr/bin/local
2. sudo cp -r /home/john/DS_Pro camp-eod  # DS_Pro is folder containing script and data
3. cd camp-eod
4. ls   # make sure that everything copied over
5. my-script.pl  # first line in script is: #!/usr/bin/perl
error: "command not found"
6. perl my-script.pl
error: Permission denied
7. sudo perl my-script.pl
program works

Questions: 
1. How do I eliminate the need to type "perl my-script.pl" into just "my-script.pl"?
2. How do I eliminate the need to type "sudo.." first?

Thank you.

---

### Post by phossal on 2007-01-06
Add this to your .bashrc 
```

#BEG Copy and Paste
export PERL_HOME='/usr/bin/perl'
PATH=.:$PERL_HOME:$PATH
#END Copy and Paste

```

Do this to your scripts:
```

chmod +x <path><script>.pl

```

If you wrote the script,and you're going to execute it, you don't need sudo.
Close your terminal windows. Reopen one, so that the .bashrc is reread.

Now try:
```

<path><script>.pl

```

It should execute. In fact, you can just click it and it will execute. (First line in script: #!/usr/bin/perl).


For my python-loving friends, the same is true:
```

#BEG Copy and Paste
export PERL_HOME='/usr/bin/perl'
export PYTHON_HOME='/usr/bin/python'
PATH=.:$PERL_HOME:$PYTHON_HOME:$PATH
#END Copy and Paste

```

---

