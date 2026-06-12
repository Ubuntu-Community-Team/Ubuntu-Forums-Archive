---
title: "man pages broken [solved]"
date: 2008-03-01
forum: General Help
---

### Post by stormzen on 2008-03-01
This was a confusing issue.  I was getting this:

[babydoll 147] media > man bash
man: invalid option -- F
usage: man [-c|-f|-k|-w|-tZT device] [-i|-I] [-adlhu7V] [-Mpath] [-Ppager]
           [-Cfile] [-Slist] [-msystem] [-pstring] [-Llocale] [-eextension]
           [section] page ...
-a, --all                   find all matching manual pages.
-d, --debug                 emit debugging messages.
-e, --extension             limit search to extension type `extension'.
-f, --whatis                equivalent to whatis.
-k, --apropos               equivalent to apropos.
-w, --where, --location     print physical location of man page(s).
-W, --where-cat,
    --location-cat          print physical location of cat file(s).
-l, --local-file            interpret `page' argument(s) as local filename(s).
-u, --update                force a cache consistency check.
-i, --ignore-case           look for pages case-insensitively (default).
-I, --match-case            look for pages case-sensitively.
-r, --prompt string         provide the `less' pager with a prompt
-c, --catman                used by catman to reformat out of date cat pages.
-7, --ascii                 display ASCII translation of certain latin1 chars.
-E, --encoding encoding     use the selected nroff device and display in pager.
-t, --troff                 use groff to format pages.
-T, --troff-device device   use groff with selected device.
-H, --html                  use lynx or argument to display html output.
-Z, --ditroff               use groff and force it to produce ditroff.
-X, --gxditview             use groff and display through gxditview (X11):
                            -X = -TX75, -X100 = -TX100, -X100-12 = -TX100-12.
-D, --default               reset all options to their default values.
-C, --config-file file      use this user configuration file.
-M, --manpath path          set search path for manual pages to `path'.
-P, --pager pager           use program `pager' to display output.
-S, --sections list         use colon separated section list.
-m, --systems system        search for man pages from other unix system(s).
-L, --locale locale         define the locale for this particular man search.
-p, --preprocessor string   string indicates which preprocessors to run.
                             e - [n]eqn   p - pic    t - tbl
                             g - grap     r - refer  v - vgrind
-V, --version               show version.
-h, --help                  show this usage message.
1 [18:17 2.49]

[babydoll 148] media > /usr/bin/man bash
No manual entry for bash
See 'man 7 undocumented' for help when manual pages are not available.

1 [18:20 0.76]
[babydoll 152] media > /usr/bin/man 7 undocumented
No manual entry for undocumented in section 7

1 [18:17 2.07]
[babydoll 150] media > alias
alias make='base-xtitle Making $(basename $PWD) ; make'
alias ncftp='base-xtitle ncFTP ; ncftp'
alias top='base-xtitle Processes on $HOST && top'


It turns out that this was a result of what was in my .bashrc:
1) a MANPATH= statement  (other threads state this path should be empty)
2) a man() function in .bashrc that I picked up from somewhere that included the -F flag.  (It's main purpose is to name the titlebar of a terminal where a manpage is being used.)  Taking out the -F  and commenting the MANPATH= statement fixed the problem.

I should point out that the whole reason why I had this problem is because I reused my /home partition and came from another distro: FC6.

---

