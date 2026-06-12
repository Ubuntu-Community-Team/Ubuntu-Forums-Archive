---
title: "A shell script to create a shell script..."
date: 2007-10-27
forum: General Help
---

### Post by dizwell on 2007-10-27
I have a script which reads, in part, 

[FONT="Courier New"]case in "$1"
start )
 -- do stuff
stop)
 -- do other stuff
*)
esac
[/FONT]

If I create that script myself, no problems: it works and everything is good. But I actually want to create a new script that reads:

[FONT="Courier New"]cat >> /etc/myscript.sh << EOF
case in "$1"
start )
 -- do stuff
stop)
 -- do other stuff
*)
esac
EOF[/FONT]

...and that ALMOST works! I mean that when I run the second script, it certainly creates the first, but in doing so it strips out the all-important "$1". Instead, I just get the line

[FONT="Courier New"]case in ""[/FONT]

My question is, therefore, how to write the second script so that it doesn't do strange things to my $1 variable and instead sees it as a literal piece of text to be inserted verbatim into the shell script it's creating.

Thanks for any pointers...
Regards
HJR

---

### Post by nick_h on 2007-10-27
Escape the $ as follows:
```
cat >> /etc/myscript.sh << EOF
case in "\$1"
start )
-- do stuff
stop)
-- do other stuff
*)
esac
EOF
```

---

### Post by dizwell on 2007-10-27
You know, I have been escaping bits and pieces of this all morning.
Double quotes, double double quotes, double single quotes, single double quotes, slash-double-quotes, slash-single-quotes. 

I must have done every possible combination... except this one, which works beautifully, so thank you very much!

---

### Post by pmg on 2007-10-28
Another approach, if you don't want any variables in the here-document (between the << and the "EOF" word) interpreted in the second script, you could put 's around the end delimiter after the << to indicate that:
```
cat >> /etc/myscript.sh << 'EOF'
case in "$1"
start )
-- do stuff
stop)
-- do other stuff
*)
esac
EOF
```

---

