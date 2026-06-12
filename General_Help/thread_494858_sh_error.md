---
title: "sh error"
date: 2007-07-07
forum: General Help
---

### Post by cragged6 on 2007-07-07
The following problem does not occur when I run from terminal, but I would like to automate through editor external program calls.

gedit and Texmaker external program calls to metapost  work fine, but under certain circumstances (b/etex ) a program, makempx, is called by metapost and I get the error:

sh: makempx: not found

and the required file cannot be made. makempx is in the same /bin folder as mpost.

This is under Fiesty, TexLive2007, and metapost 1.00 (most recent), and required PATH is set in .bashrc.  Again, when I process the file from terminal all goes well. Something with  Ubuntu or do I need bash help?

---

### Post by bettlebrox on 2007-07-07
I'm not quiet sure what your trying to do, but try using the full path to the command:

/usr/bin/makempx

---

### Post by cragged6 on 2007-07-07
makempx is called by mpost (metapost)

From a text editor the full path is given to /usr/.../mpost which runs fine on a simple file, however, when that file also needs to be processed by makempx, mpost calls it and the error results.

When processed from command line as

```
$ mpost {file}
```

all is well--makempx is called and succeeds, when it fails to be found from the editor call.

---

### Post by Mr. C. on 2007-07-07
> **cragged6 said:**
> 
sh: makempx: not found


This is a simple PATH problem.

Also note the difference in the program name when bash vs. sh is used:

```
$ bash
$ nosuchprog
bash: nosuchprog: command not found
$ sh
$ nosuchprog 
sh: nosuchprog: command not found
```

The "sh" shell does not look for .bashrc files; it looks for .profile.  Any PATH settings you need to make must be there if your calling programs use sh vs. bash.  Setup PATH correctly in .profile.  But this may not be sufficient.

Because there are programs which do the invoking of your metapost program, you need to be sure their environment is setup correctly (some setup PATH explicitly).  Review any installation instructions or README files that are available for that software.

MrC

---

### Post by cragged6 on 2007-07-07
> **Mr. C. said:**
> This is a simple PATH problem.

The "sh" shell does not look for .bashrc files; it looks for .profile.  Any PATH settings you need to make must be there if your calling programs use sh vs. bash.  Setup PATH correctly in .profile.  But this may not be sufficient.

Because there are programs which do the invoking of your metapost program, you need to be sure their environment is setup correctly (some setup PATH explicitly).  Review any installation instructions or README files that are available for that software.


Thank you MrC for the .profile tip. I knew that sh would not look for .bashrc (although I did not find a way around it) however, the problem persists.

I am still ignorant as to why:

running $ mpost {file} from the command line works--whatever mpost does to get makempx works then--but using External  Tools>Run command from gedit (for example)

/usr/local/texlive/2007/bin/i386-linux/mpost "$GEDIT_CURRENT_DOCUMENT_NAME" 

will compile a file that does not need the call to makempx, but fails when that call is needed. (Texmaker editor does same thing.)

I will continue to check regarding environment setups, but the gedit help has called it a bash issue, and I await response from metapost people...kinda going in circles at the moment, but thanks for the response.

Perhaps I am being over simplistic, but it seems that if mpost calls makempx correctly from the command line, and starting mpost from within an editor works on files where mpost makes no call, it should also work when it needs to make a call. Thanks again.

---

### Post by Mr. C. on 2007-07-07
What are the permissions to and exact path of the makempx program ?

MrC

---

### Post by Mr. C. on 2007-07-07
I took a quick look at the INSTALL manual.  It says:

> Set up PATH:
===========
Set up your PATH to include the directory containing the just installed
binaries (e.g. /usr/local/teTeX/bin/i686-pc-linux-gnu); similarly, MANPATH
and INFOPATH to include the relevant newly installed subdirectories,
i.e. $prefix/man resp. $prefix/info. To avoid conflicts with a
possible different TeX installation, make sure to put the new directories
first. E.g. for setting PATH, use something like the following, but
replace i686-pc-linux-gnu by your actual platform directory:
  PATH=/usr/local/teTeX/bin/i686-pc-linux-gnu:$PATH; export PATH
or
  setenv PATH /usr/local/teTeX/bin/i686-pc-linux-gnu:$PATH

As an alternative to adjust PATH, you could as well create symbolic
links in a standard location such as /usr/local/bin:

    Example using GNU-ls (which supports the "force" option):
      ln -sf /usr/local/teTeX/bin/i686-pc-linux-gnu/* /usr/local/bin

    Example using standard ln:
      (cd /usr/local/teTeX/bin/i686-pc-linux-gnu; echo *) \
        | (cd /usr/local/bin; xargs rm -f)
      ln -s /usr/local/teTeX/bin/i686-pc-linux-gnu/* /usr/local/bin

Check environment
=================
Note, that the run-time search paths for all programs that use
the Kpathsea library can be configured by changing the paths in
TEXMFMAIN/web2c/texmf.cnf and changes to these paths does not require
to recompile any of the programs. Therefore, you hardly need to set
extra environment variables. If you define some environment variables,
they overrule the search paths in texmf.cnf unless they have an empty
path component (i.e. a colon at the beginning or end or a doubled colon
in the middle).

The variables to check are:
  AFMFONTS BIBINPUTS BSTINPUTS DVILJFONTS DVIPSFONTS DVIPSHEADERS GFFONTS
  GLYPHFONTS INDEXSTYLE MFBASES MFINPUTS MFPOOL MFTINPUTS MPINPUTS
  MPMEMS MPPOOL MPSUPPORT OCPINPUTS OFMFONTS OPLFONTS OTPINPUTS OVFFONTS
  OVPFONTS PKFONTS PSHEADERS T1FONTS T1INPUTS TEXBIB TEXCONFIG TEXDOCS
  TEXFONTMAPS TEXFONTS TEXFORMATS TEXINDEXSTYLE TEXINPUTS TEXMFCNF
  TEXMFDBS TEXMFINI TEXPICTS TEXPKS TEXPOOL TEXPSHEADERS TEXSOURCES
  TFMFONTS TRFONTS VFFONTS XDVIFONTS XDVIVFS

A simple way to check them is to run
  texconfig conf
once you have set up your PATH. Be careful if some variables are non-empty
and have a look at the locations of the binaries. Not all binaries are
checked, only some.

Have you verified this is correcty ?

---

### Post by cragged6 on 2007-07-07
MrC,

The path to both is:

/usr/local/texlive/2007/bin/i386-linux

I have permission to read and write all;  my group (does not exist--it's my laptop only ;-})  has read only.

Is the INSTALL man you refer to teTex? Some things are similar, but I use TexLive. 

Yes to checking the kpathsea and web2c/texmf.cnf files, plus .bashrc, otherwise it wouldn't work from the command line.  Also have run texhash which is another detail to maintaining *Tex installs.

Am checking into the hidden gedit files for clues on how the calls are set up--errors from using the gui maybe--but nothing yet--also perplexing as the other editor (Texmaker) shows same problem.

Thanks for your input.

---

### Post by Mr. C. on 2007-07-07
The doc I found was for teTex, not TexLive.

Again, you mention .bashrc.  You need to setup your PATH correctly in .profile.  It is clear that sh is being called by the parent program.

There are only two mechanisms the system uses to find a program to run:

[LIST=1]
[*]by using a full or relative path
[*]by using an simple command name (contains no path components)
[/LIST]

It is clear from the error message that (2) is being used.  This indicates there is a PATH problem with the invoking program (which is sh in this case).  Focus your attention there.

MrC

---

### Post by cragged6 on 2007-07-07
> **Mr. C. said:**
> The doc I found was for teTex, not TexLive.

Again, you mention .bashrc.  You need to setup your PATH correctly in .profile.  It is clear that sh is being called by the parent program.

There are only two mechanisms the system uses to find a program to run:

[LIST=1]
[*]by using a full or relative path
[*]by using an simple command name (contains no path components)
[/LIST]

It is clear from the error message that (2) is being used.  This indicates there is a PATH problem with the invoking program (which is sh in this case).  Focus your attention there.

MrC

Agreed, and perhaps the metapost folks can help with that  PATH problem, but I still have to wonder:

Why would the parent program allow the system to find a program when run from the command line but not when the parent program is run from a text editor...even though the parent program works when run by the text editor except when it needs to run another program?

Sorry if the logic of that question comes from the babbling mouths of babes. I can see that it would fail at step 1 from the command line by user or path error, but in my case it  does not. I can see that it might fail from user error with the text editor call setup, but it does not...until the called program needs to make a subsequent call.

I had put the PATH into .profile from your first suggestion, but no positive result.

thanks,

craggy

---

### Post by Mr. C. on 2007-07-07
Simple answer.

Consider what happens if your text editor program explicitly sets PATH and calls "sh" to spawn subprograms (which I"m sure it does, for globbing purposes), and invokes the parent program with a full path.  Eg:

gedit:

  exec "sh -c /full/path/to/parentprog"

and consider if parentprog tries to exec childprog as:

  exec "sh -c childprog"

Guess what, sh will complain it can't find childprog.  And if childprog is not needed to be called, there's no problem.

It works on your command line because your PATH is set, and there is no intermediary (gedit) that may be reset the path.

A common example of this type of failure is seen with cron, where cron sets its own path for security, and users flounder trying to figure out whey their programs work just fine from the command line, but accuse cron of being broken because their programs fail in mysterious ways when run via cron.  They fail to provide sufficient error diagnostics when a program cannot be exec'd.

In your situation, the error diagnostic is perfectly clear:

```
sh: makempx: not found
```

*always* means **sh** cannot find an executable program named **makempx** in its current PATH.

A way for you to test out the value of PATH is to replace your parentprog which you call with gedit by a quick wrapper script, such as:

/path/to/parentprog:

```
#!/bin/sh

echo $PATH
exit 0
```

and then use gedit as you normally would.  Examine the output.

MrC

---

### Post by cragged6 on 2007-07-07
> **Mr. C. said:**
> Simple answer.

Consider what happens if your text editor program explicitly sets PATH and calls "sh" to spawn subprograms (which I"m sure it does, for globbing purposes), and invokes the parent program with a full path.
....

It works on your command line because your PATH is set, and there is no intermediary (gedit) that may be reset the path.

In your situation, the error diagnostic is perfectly clear:

```
sh: makempx: not found
```

*always* means **sh** cannot find an executable program named **makempx** in its current PATH.

A way for you to test out the value of PATH is to replace your parentprog which you call with gedit by a quick wrapper script, such as:

/path/to/parentprog:

```
#!/bin/sh

echo $PATH
exit 0
```

and then use gedit as you normally would.  Examine the output.

MrC

Sha-Bang MrC! And a very clear explanation, thank you for the effort. (I will henceforth keep globbing in mind.)

I did not carefully consider that the calling program would maintain a change in the path (despite the thumpings of advice). Attempts to adjust my problem via the gui had become frustrating but your guidance sent me to the .gnome2 files for gedit and it was easier to establish the correct path from there.

Putting:

#!/bin/sh
PATH=/usr/local/texlive/2007/bin/i386-linux:$PATH; export PATH
/usr/local/texlive/2007/bin/i386-linux/mpost "$GEDIT_CURRENT_DOCUMENT_NAME"

in the gedit External Tool shell script...paved the path.

I anticipate finding similar success with the Texmaker editor. Thanks again,

Craggy

---

