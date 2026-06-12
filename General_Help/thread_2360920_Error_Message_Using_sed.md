---
title: "Error Message Using sed"
date: 2017-05-09
forum: General Help
---

### Post by John_Patrick_Mason on 2017-05-09
I'm currently learning about the Linux command line through William E. Shotts's *The Linux Command Line*. I'm stuck at [page 335]("https://sourceforge.net/projects/linuxcommand/files/TLCL/16.07/TLCL-16.07.pdf/download") when it asks me to input the following command:
```

sort -k 1,1 -k 2n distros.txt | sed -f distros-nl.sed | nl

```

When I input the above command, I get the following error:

```

sed: file distros-nl.sed line 10: unknown command: `\'

```

This is what my distros.txt file looks like:

```

SUSE    10.2    12/07/2006
Fedora    10    11/25/2008
SUSE    11.0    06/19/2008
Ubuntu    8.04    04/24/2008
Fedora    8    11/08/2007
SUSE    10.3    10/04/2007
Ubuntu    6.10    10/26/2006
Fedora    7    05/31/2007
Ubuntu    7.10    10/18/2007
Ubuntu    7.04    04/19/2007

```

And, this, is what my distros-nl.sed file looks like:

```

# sed script to produce Linux distributions report

1 i\
\\:\\:\\:\
\
Linux Distributions Report\
\
Name    Ver.     Released\
----    ----     --------\    
\\:\\:
s/\([0-9]\{2\}\)\/\([0-9]\{2\}\)\/\([0-9]\{4\}\)$/\3-\1-\2/
$ a\
\\:\
\
End of Report

```

How can I get this to work?

---

### Post by steeldriver on 2017-05-09
When using backslash characters for line continuation, they MUST be the last characters on the line - your line 9 has trailing whitespace after the \ (visible using `cat -net`): 

```

$ cat -net your-distros-nl.sed
     1  # sed script to produce Linux distributions report$
     2  $
     3  1 i\$
     4  \\:\\:\\:\$
     5  \$
     6  Linux Distributions Report\$
     7  \$
     8  Name    Ver.     Released\$
[COLOR=#ff0000]     9  ----    ----     --------\    $[/COLOR]
    10  \\:\\:$
    11  s/\([0-9]\{2\}\)\/\([0-9]\{2\}\)\/\([0-9]\{4\}\)$/\3-\1-\2/$
    12  $ a\$
    13  \\:\$
    14  \$
    15  End of Report$

```

---

### Post by John_Patrick_Mason on 2017-05-09
Thanks. I just got it to work. I don't think the book mentions anything about trailing whitespaces.

---

