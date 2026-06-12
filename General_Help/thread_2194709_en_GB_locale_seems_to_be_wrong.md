---
title: "en_GB locale seems to be wrong"
date: 2013-12-20
forum: General Help
---

### Post by marty4 on 2013-12-20
It seems as though the en_GB locale is wrong, it is providing certain dates in the wrong format:

(%a %b %d %T %Z %Y)
root@home:~# date
Fri Dec 20 11:18:54 GMT 2013

I've definitely got the locale set to en_GB:


root@home:~# locale
LANG=en_GB.UTF-8
LANGUAGE=en_GB:en
LC_CTYPE="en_GB.UTF-8"
LC_NUMERIC="en_GB.UTF-8"
LC_TIME="en_GB.UTF-8"
LC_COLLATE="en_GB.UTF-8"
LC_MONETARY="en_GB.UTF-8"
LC_MESSAGES="en_GB.UTF-8"
LC_PAPER="en_GB.UTF-8"
LC_NAME="en_GB.UTF-8"
LC_ADDRESS="en_GB.UTF-8"
LC_TELEPHONE="en_GB.UTF-8"
LC_MEASUREMENT="en_GB.UTF-8"
LC_IDENTIFICATION="en_GB.UTF-8"
LC_ALL=

I've checked on OSX and that is actually providing it correctly:


Martys-MacBook-Air:~ Marty$ date
Fri 20 Dec 2013 11:18:57 GMT

I've attempted to edit the en_GB locale file but cannot seem to get it set correctly, how can I do this/report it as a bug to get it fixed?

---

### Post by btindie on 2013-12-20
Which file did you edit? /usr/share/i18n/locales/en_GB ?

And did you run
```
sudo locale-gen en_GB.UTF-8
```
once you'd made your changes to recompile the locale?

As for why the default for the British English locale is in yankie format I have no idea... just one of those irritating things, but you can change it.

I've also changed
```
d_fmt       "<U0025><U0064><U002F><U0025><U006D><U002F><U0025><U0079>"
```
to
```
d_fmt       "<U0025><U0064><U002F><U0025><U006D><U002F><U0025><U0059>"
```
so it display the year with 4 digits instead of 2 when using '%x' - e.g. ```
date +%x
```

**Edit:** It looks like it may be that way as your MacBook is defaulting to using "locale's date and time" %c

If you do ```
date +%c
``` on Ubuntu it'll display it in exactly the same format as your MacBook.

In the locale file, %c uses d_t_fmt and the default (on Ubuntu) uses date_fmt.

---

### Post by ajgreeny on 2013-12-20
Interesting, and I hadn't noticed this before, but it looks as if all the variables are reporting in the wrong order on my Xubuntu 12.04.3 64bit system, as well as yours, though mine is set differently (%a, %d %b - %H:%M) and only the %b & %d are wrong way round, showing **Fri, Dec 20 - 12:58**.

What OS version are you running?

---

### Post by marty4 on 2013-12-20
I ran locale-gen and restarted, let me give that a try

I'm running 13.10 x64, but this seems to happen in Debian as well, at least in the latest Raspbian.

How would I go about reporting it for correction?

---

### Post by marty4 on 2013-12-20
That seems to have worked, it now displays:

root@home:/usr/share/i18n/locales# date
Fri 20 Dec 13:22:49 GMT 2013

I changed:
```
date_fmt        "<U0025><U0061><U0020><U0025><U0062><U0020><U0025><U0065>/<U0020><U0025><U0048><U003A><U0025><U004D><U003A><U0025><U0053><U0020>/
<U0025><U005A><U0020><U0025><U0059>"
```

To:
```
date_fmt        "<U0025><U0061><U0020><U0025><U0065><U0020><U0025><U0062>/<U0020><U0025><U0048><U003A><U0025><U004D><U003A><U0025><U0053><U0020>/
<U0025><U005A><U0020><U0025><U0059>"
```

EDIT:

Still seems broken when you list files though, is that under a different locale item?

-rw-r--r-- 1 root root    2244 Mar  6  2012 en_AG
-rw-r--r-- 1 root root    5277 Mar 22  2013 en_AU
-rw-r--r-- 1 root root    2574 Mar  6  2012 en_BW
-rw-r--r-- 1 root root    5795 Mar 22  2013 en_CA
-rw-r--r-- 1 root root    3742 Mar 22  2013 en_DK
-rw-r--r-- 1 root root    5340 Dec 20 13:22 en_GB
-rw-r--r-- 1 root root    6921 Mar 22  2013 en_HK
-rw-r--r-- 1 root root    4978 Mar 22  2013 en_IE
-rw-r--r-- 1 root root    1492 Mar  6  2012 en_IE@euro
-rw-r--r-- 1 root root    6330 Mar 22  2013 en_IN
-rw-r--r-- 1 root root    8772 Mar  6  2012 en_NG
-rw-r--r-- 1 root root    5243 Mar 22  2013 en_NZ
-rw-r--r-- 1 root root    6886 Mar 22  2013 en_PH
-rw-r--r-- 1 root root    6638 Mar 22  2013 en_SG
-rw-r--r-- 1 root root    5577 Mar  6  2012 en_US
-rw-r--r-- 1 root root   11102 Mar 22  2013 en_ZA
-rw-r--r-- 1 root root    1855 Mar  6  2012 en_ZM
-rw-r--r-- 1 root root    2548 Mar  6  2012 en_ZW

---

### Post by btindie on 2013-12-20
> **marty4 said:**
> 
Still seems broken when you list files though, is that under a different locale item?

-rw-r--r-- 1 root root    2244 Mar  6  2012 en_AG
-rw-r--r-- 1 root root    5277 Mar 22  2013 en_AU
-rw-r--r-- 1 root root    2574 Mar  6  2012 en_BW
-rw-r--r-- 1 root root    5795 Mar 22  2013 en_CA

That works slightly differently...

From "man ls"
>        --time-style=STYLE
              with  -l, show times using style STYLE: full-iso, long-iso, iso,
              locale, +FORMAT.  FORMAT is interpreted like `date';  if  FORMAT
              is  FORMAT1<newline>FORMAT2, FORMAT1 applies to non-recent files
              and FORMAT2 to recent files; if STYLE is prefixed with `posix-',
              STYLE takes effect only outside the POSIX locale

From the source to *ls* the default time style is set to the following:
```
static char const *long_time_format[2] =
  {
    N_("%b %e  %Y"),
    N_("%b %e %H:%M")
  };
```
[COLOR=#000000]By default "ls -l" will use the --time-style= option passed, if undefined it uses the TIME_STYLE environment variable and if that's undefined it uses 'locale' as the default. That 'locale' doesn't appear to do anything other than use the built in default. Ref [here]("http://www.gnu.org/software/coreutils/manual/html_node/Formatting-file-timestamps.html"). You can override it by setting the TIME_STYLE environment variable:[/COLOR]
```
[FONT=Verdana]export TIME_STYLE="+%e %b  %Y
[/FONT][FONT=Verdana]%e %b %H:%M"[/FONT]
```
which will then display it the correct way around. Note the newline within the variable.

> [COLOR=#222222][FONT=Verdana]-rw-r--r-- 1 root root    7745  4 Apr  2012 aa_DJ
[/FONT][/COLOR][COLOR=#222222][FONT=Verdana]-rw-r--r-- 1 root root    6568  4 Apr  2012 aa_ER
[/FONT][/COLOR][COLOR=#222222][FONT=Verdana]-rw-r--r-- 1 root root    5981  4 Apr  2012 aa_ER@saaho
[/FONT][/COLOR][COLOR=#222222][FONT=Verdana]-rw-r--r-- 1 root root    6687  4 Apr  2012 aa_ET[/FONT][/COLOR]

---

### Post by marty4 on 2013-12-20
Awesome, thanks.

How can I report the initial locale issue?

---

