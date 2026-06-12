---
title: "perl script not recognize standard shell commands"
date: 2014-03-21
forum: General Help
---

### Post by keith14 on 2014-03-21
Hi,I using perl script that tries to copy but I get error message:
sh: 1: cp -r /home/keith/bin /home/keith/MY_S/home_dir: not found
sh: 1: cp /home/keith/.kshrc /home/keith/MY_S/home_dir/dot_kshrc: not found
sh: 1: cp /home/keith/.bashrc /home/keith/MY_S/home_dir/dot_bashrc: not found
section of perl script:
if ($OS=~/Ubuntu/) {  if (-d "$HOME/MY_S") {   `"cp -r $HOME/bin $HOME/MY_S/home_dir"`;
   `"cp $HOME/.kshrc $HOME/MY_S/home_dir/dot_kshrc"`;
   `"cp $HOME/.bashrc $HOME/MY_S/home_dir/dot_bashrc"`;                       }                     }
these files exist Y am I getting error message?
Thanks,Keith

---

### Post by TheFu on 2014-03-21
Looks like perl isn't running. What is the 1st line?

---

### Post by drmrgd on 2014-03-21
The problem is the use of quotes with backticks.  If you want to run a system command with backticks you don't need to use the quotation marks in there.  The correct script should be:

```

if ($OS=~/Ubuntu/) { 
    if (-d "$HOME/MY_S") { 
        `cp -r $HOME/bin $HOME/MY_S/home_dir`;
        `cp $HOME/.kshrc $HOME/MY_S/home_dir/dot_kshrc`;
        `cp $HOME/.bashrc $HOME/MY_S/home_dir/dot_bashrc`; 
    } 
}

```

---

### Post by keith14 on 2014-03-21
Hi,
Yes, removing qq fixed the problem. This is strange I use qq on win-xp and win8 boot. I have two machines that boot in both xp and win8. I use mks toolkit there, and perl from activeperl. Rasberry perl has a lot of over head so I use activeperl.
Thanks,
Keith

---

### Post by TheFu on 2014-03-22
> **keith14 said:**
> Hi,
Yes, removing qq fixed the problem. This is strange I use qq on win-xp and win8 boot. I have two machines that boot in both xp and win8. I use mks toolkit there, and perl from activeperl. Rasberry perl has a lot of over head so I use activeperl.
Thanks,
Keith

ActivePerl was great years ago, but it has many non-portable aspects.
Strawberry Perl is a direct port to win32 from the normal perl source - it has fewer strange behaviors, IMHO. This is better if cross-platform perl is the desire.

---

### Post by drmrgd on 2014-03-22
For portability with such things, you might try File::Copy.  It's a core module that I'm pretty sure works well under Windows and handles a lot of the OS specific directory structure stuff (I don't have a Windows machine immediately in front of me to test).  You might also need File::Copy::Recursive for the first copy command, which may not be a core module, but I know it works well under Windows for the most part.  So, one way to do this is:

```

use File::Copy;
use File::Copy::Recursive qw{ dircopy };

if ( $OS eq "Ubuntu" ) { 
    if ( -d "$ENV{'HOME'}/MY_S" ) {
        my $home = $ENV{'HOME'};
        my $dest = "$home/MY_S";
        dircopy( "$home/bin", "$dest/home_dir" );
        copy( "$home/.kshrc", "$dest/home_dir" );
        copy( "$home/.bashrc", "$dest/home_dir" );
    }
}

```
In general if you can find a core Perl module to do such system tasks you take a lot of the guess work out of the OS specific stuff that can cause some portability problems.

---

### Post by TheFu on 2014-03-22
File::Copy works on Strawberry Perl under Windows.  It should work with Active-Perl too, but haven't used that in about 8 yrs.

---

