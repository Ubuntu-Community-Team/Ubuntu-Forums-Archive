---
title: "Can not enable pango in Firefox"
date: 2006-12-20
forum: General Help
---

### Post by zmr on 2006-12-20
There has been considerable discussion about enabling or disabling pango in Firefox in order to increase performance. I need pango enabled in Firefox 2 in order to properly display complex scripts in Tibetan. I have been using the following command line to enable pango on Firefox 1.5:
MOZ_DISABLE_PANGO=0 firefox

This works more or less fine for Firefox 1.5 (though it does not enable pango permanently-- you need to run the script again anytime you want to enable pango). The command line is not working in Firefox 2.0 (I am using Dapper. I updated to Firefox 2 using the script provided [[COLOR="Blue"]here[/COLOR]]("http://www.psychocats.net/ubuntu/firefox"))

Does anyone have any insight on what the problem might be?

---

### Post by kerry_s on 2006-12-20
Have you tried adding it to /etc/enviroment?

sudo gedit /etc/enviroment

---

### Post by zmr on 2006-12-20
Do you mean adding Tibetan to the environment? Or somehow work doing something with Pango therein? This is the text presently in /etc/environment:

```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11$
LANG="en_US.UTF-8"
LANGUAGE="en"

```

Maybe I could add Dzongkha (basically Tibetan) to the Language setting. Is it possible to specify two languages in the environment settings? I am not clear on how the environment settings work...

---

### Post by kerry_s on 2006-12-20
> **zmr said:**
> Do you mean adding Tibetan to the environment? Or somehow work doing something with Pango therein? This is the text presently in /etc/environment:

```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11$
LANG="en_US.UTF-8"
LANGUAGE="en"

```

Maybe I could add Dzongkha (basically Tibetan) to the Language setting. Is it possible to specify two languages in the environment settings? I am not clear on how the environment settings work...


```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11$
LANG="en_US.UTF-8"
LANGUAGE="en"
MOZ_DISABLE_PANGO=0 

```

---

### Post by zmr on 2006-12-20
Thank you. I added MOZ_DISABLE_PANGO=0 to  /etc/environment. Unfortunately, this still does not solve the problem; nothing has changed.

---

### Post by kerry_s on 2006-12-21
> **zmr said:**
> Thank you. I added MOZ_DISABLE_PANGO=0 to  /etc/environment. Unfortunately, this still does not solve the problem; nothing has changed.

It might be the difference in the build, i think i read that firefox 2 is built using cairo instead of pango. Maybe check the mozilla site for information, Sorry i couldn't help.

---

### Post by chandra on 2006-12-22
I have the same problem.  With the page

[http://tinyurl.com/pk38t](http://tinyurl.com/pk38t)

or 

[http://en.wikipedia.org/wiki/Wikipedia:Enabling_complex_text_support_for_Indic_scripts](http://en.wikipedia.org/wiki/Wikipedia:Enabling_complex_text_support_for_Indic_scripts)

I can see the complex Indic scripts correctly rendered with Konqueror but not with Firefox 2.

I have tried both 

MOZ_DISABLE_PANGO=0 firefox

and

MOZ_ENABLE_PANGO=1 firefox

and neither seems to work.

FYI, for the standard Ubuntu Firefox installed on my system, about:buildconfig gives:

-------------
Configure arguments
--host=i486-linux-gnu --build=i486-linux-gnu --prefix=/usr '--mandir=${prefix}/share/man' '--infodir=${prefix}/share/info' --enable-default-toolkit=gtk2 --with-default-mozilla-five-home=/usr/lib/firefox --enable-pango --with-user-appdir=.mozilla --with-system-png=/usr --with-system-jpeg=/usr --disable-mailnews --disable-composer --disable-ldap --enable-postscript --disable-installer --disable-xprint --enable-crypto --disable-strip --disable-strip-libs --enable-canvas --enable-svg --enable-svg-renderer=cairo --enable-system-cairo --enable-mathml --disable-tests --disable-gtktest --disable-debug --enable-xft '--enable-optimize=-pipe\ -w\ -O2\ -g\ -fno-strict-aliasing' --with-system-zlib=/usr --without-system-nspr --enable-xinerama --enable-extensions=default --disable-pedantic --disable-long-long-warning --enable-single-profile --disable-profilesharing --enable-gnomevfs --enable-application=browser --disable-installer --disable-updater --enable-chrome-format=flat --disable-elf-dynstr-gc --enable-system-myspell --with-distribution-id=com.ubuntu 
-------------

I do not know how, if at all, pango and cairo interact, but the result is that complex Indic scripts are rendered incorrectly in Firefox.

I might file a bug report at Launchpad for this, if it has not already been done so.

Any help most appreciated.

---

### Post by zmr on 2006-12-22
I ran Firefox 1.5 just now after setting the /etc/environment as you suggested and indeed 1.5 displays the scripts fine. Firefox 2.0 still does not render them correctly, so maybe it is just as you say-- that FF2 was not built with pango. I am looking into this at the web forums on mozilla now. Thank you for your help.

---

### Post by dushkal on 2007-01-29
Hi,

I'm not sure if this is too late (the thread is more than a month old...) but installing the locale files help in this case. firefox script checks in /var/lib/locales/supported.d/ if the locale is supported or not and then sets the MOZ_DISABLE_PANGO So, adding the locale in the supported list would enable the support here....

Otherwise you could modify the firefox script..

```

if [ "x${MOZ_DISABLE_PANGO}" = x ]; then
    if egrep '^(bn|gu|hi|kn|ml|mr|ne|pa|si|ta|te)_' \
        /var/lib/locales/supported.d/*[^~] >/dev/null 2>&1; then
        MOZ_DISABLE_PANGO=0
    else
        MOZ_DISABLE_PANGO=1
    fi
    export MOZ_DISABLE_PANGO
fi
if [ "x${MOZ_DISABLE_PANGO}" = x0 ]; then
    unset MOZ_DISABLE_PANGO
fi

```

you could modify this piece in /usr/bin/firefox to suite your needs and you would be fine...
I checked this with feisty, and installing mr locale enables the pango support in FF....

just my 2 cents...:)

---

### Post by godlessgeek on 2007-09-17
> **chandra said:**
> I have the same problem.  With the page

[http://tinyurl.com/pk38t](http://tinyurl.com/pk38t)

or 

[http://en.wikipedia.org/wiki/Wikipedia:Enabling_complex_text_support_for_Indic_scripts](http://en.wikipedia.org/wiki/Wikipedia:Enabling_complex_text_support_for_Indic_scripts)

I can see the complex Indic scripts correctly rendered with Konqueror but not with Firefox 2.

I have tried both 

MOZ_DISABLE_PANGO=0 firefox

and

MOZ_ENABLE_PANGO=1 firefox

and neither seems to work.

FYI, for the standard Ubuntu Firefox installed on my system, about:buildconfig gives:

-------------
Configure arguments
--host=i486-linux-gnu --build=i486-linux-gnu --prefix=/usr '--mandir=${prefix}/share/man' '--infodir=${prefix}/share/info' --enable-default-toolkit=gtk2 --with-default-mozilla-five-home=/usr/lib/firefox --enable-pango --with-user-appdir=.mozilla --with-system-png=/usr --with-system-jpeg=/usr --disable-mailnews --disable-composer --disable-ldap --enable-postscript --disable-installer --disable-xprint --enable-crypto --disable-strip --disable-strip-libs --enable-canvas --enable-svg --enable-svg-renderer=cairo --enable-system-cairo --enable-mathml --disable-tests --disable-gtktest --disable-debug --enable-xft '--enable-optimize=-pipe\ -w\ -O2\ -g\ -fno-strict-aliasing' --with-system-zlib=/usr --without-system-nspr --enable-xinerama --enable-extensions=default --disable-pedantic --disable-long-long-warning --enable-single-profile --disable-profilesharing --enable-gnomevfs --enable-application=browser --disable-installer --disable-updater --enable-chrome-format=flat --disable-elf-dynstr-gc --enable-system-myspell --with-distribution-id=com.ubuntu 
-------------

I do not know how, if at all, pango and cairo interact, but the result is that complex Indic scripts are rendered incorrectly in Firefox.

I might file a bug report at Launchpad for this, if it has not already been done so.

Any help most appreciated.

Here's what worked for me.

Go to System > Administration > Language support

Tick the check mark for "Enable support to enter complex scripts" and in the list tick the check mark for "Marathi" (or Hindi I suppose)

This not only solved my problem of Indic scripts but also (quite miraculously) Firefox started rendering Windows fonts (Arial, Tahoma etc.) more truly!

Btw I did this on Feisty

---

