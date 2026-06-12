---
title: "VMD ./configure Fails on Four"
date: 2007-05-26
forum: General Help
---

### Post by falciron on 2007-05-26
I just downloaded the latest .tar.gz file for VMD in order to get a final project done for Chemistry. I got the right one, a Linux AMD64 release, but for some reason, I can't even get past the ./configure step. Here are the errors:

```
[COLOR="Red"]blank@bLANK:~/vmd-1.8.6$ sh ./configure[/COLOR]
./configure: 13: =: not found
./configure: 16: =/usr/local/bin: not found
./configure: 19: =/usr/local/lib/: not found
./configure: 23: Syntax error: "{" unexpected (expecting "then")
```

Any idea what I might need to do to get to the next step? The installation guides say that I can modify some of the parameters, and these include:

```
# Name of shell script used to start program; this is the name used by users
$install_name = "vmd";

# Directory where VMD startup script is installed, should be in users' paths.
$install_bin_dir="/usr/local/bin";

# Directory where VMD files and executables are installed
$install_library_dir="/usr/local/lib/$install_name";

# optionally override hard-coded defaults above with environment variables
if ($ENV{VMDINSTALLNAME}) {
  $install_name = $ENV{VMDINSTALLNAME}
}
if ($ENV{VMDINSTALLBINDIR}) {
  $install_bin_dir = $ENV{VMDINSTALLBINDIR}
}
if ($ENV{VMDINSTALLLIBRARYDIR}) {
  $install_library_dir = $ENV{VMDINSTALLLIBRARYDIR}
}
```

I can provide anything else necessary for this installation. If this problem isn't solvable, I guess I will get to learn how to use Blender in four days.;)

---

### Post by taurus on 2007-05-26
What happens when you run this from a terminal?

```
ls -la /usr/local
```

---

### Post by falciron on 2007-05-26
Here's the result that you requested:

```
total 36
drwxr-xr-x  9 root root 4096 2006-10-25 08:26 .
drwxr-xr-x 12 root root 4096 2007-04-28 11:36 ..
drwxr-xr-x  2 root root 4096 2007-05-13 23:10 bin
drwxr-xr-x  2 root root 4096 2006-10-25 08:26 games
drwxr-xr-x  4 root root 4096 2007-05-13 23:06 include
drwxr-xr-x  8 root root 4096 2007-05-25 17:12 lib
lrwxrwxrwx  1 root root    9 2007-04-26 13:08 man -> share/man
drwxr-xr-x  2 root root 4096 2006-10-25 08:26 sbin
drwxr-xr-x 15 root root 4096 2007-05-13 23:10 share
drwxr-xr-x  2 root root 4096 2006-10-25 08:26 src
```

---

### Post by taurus on 2007-05-26
> **falciron said:**
> Here's the result that you requested:

```
total 36
drwxr-xr-x  9 root root 4096 2006-10-25 08:26 .
drwxr-xr-x 12 root root 4096 2007-04-28 11:36 ..
[COLOR="Blue"]drwxr-xr-x  2 root root 4096 2007-05-13 23:10 bin[/COLOR]
drwxr-xr-x  2 root root 4096 2006-10-25 08:26 games
drwxr-xr-x  4 root root 4096 2007-05-13 23:06 include
[COLOR="Blue"]drwxr-xr-x  8 root root 4096 2007-05-25 17:12 lib[/COLOR]
lrwxrwxrwx  1 root root    9 2007-04-26 13:08 man -> share/man
drwxr-xr-x  2 root root 4096 2006-10-25 08:26 sbin
drwxr-xr-x 15 root root 4096 2007-05-13 23:10 share
drwxr-xr-x  2 root root 4096 2006-10-25 08:26 src
```

Well, there are your /usr/local/bin & /usr/local/lib so I don't know why it complains about missing those two directories.

Can you post the configure file here?

```
cat configure
```

---

### Post by falciron on 2007-05-27
It's too long to post in one thread, and too large to attach. Is there a specific part that you want or can you think of some other way to get it hosted?

---

### Post by Bachstelze on 2007-05-27
```
sudo dpkg-reconfigure dash
```

it will ask if you want to use Dash, say no then try to run *./configure* again.

---

### Post by falciron on 2007-05-27
Here's what I received after doing what you suggested, HymnToLife.

```
blank@bLANK:~/vmd-1.8.6$ ./configure
using configure.options: LINUXAMD64 OPENGL FLTK TK ACTC IMD SPACEBALL LIBTACHYON VRPN NETCDF TCL PYTHON PTHREADS NUMPY SILENT
blank@bLANK:~/vmd-1.8.6$
```

---

### Post by Bachstelze on 2007-05-27
That's not how configure scripts usually work but I don't know about yours. Maybe read the README and see it that's what it expects.

---

### Post by falciron on 2007-05-27
Forgot the sh part.

Here's what was produced when it was included.

```

[COLOR="Red"]blank@bLANK:~/vmd-1.8.6$ sh ./configure[/COLOR]
./configure: line 13: =: command not found
./configure: line 16: =/usr/local/bin: No such file or directory
./configure: line 19: =/usr/local/lib/: No such file or directory
./configure: line 23: syntax error near unexpected token `{'
./configure: line 23: `if ($ENV{VMDINSTALLNAME}) {'
```

---

