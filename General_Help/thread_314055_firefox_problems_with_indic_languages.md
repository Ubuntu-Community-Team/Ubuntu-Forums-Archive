---
title: "firefox problems with indic languages"
date: 2006-12-07
forum: General Help
---

### Post by pillu on 2006-12-07
Firefox does not render indic languages (eg. Hindi) written in the Devnagri script correctly. Example on wikipedia Hindi [http://hi.wikipedia.org]("http://hi.wikipedia.org")

This problem seems generic to firefox. These websites render much better in IE under windows. I have tried enabling Pango for firefox using
```
 MOZ_DISABLE_PANGO=0 firefox
```
to no avail.

Please help me with a fix if you have one or suggest an alternate browser for linux that has better support for other languages.

---

### Post by zmr on 2006-12-12
I am having the exact same problem with Tibetan scripts. Setting  MOZ_DISABLE_PANGO=0 firefox has no effect (I am using Firefox and Swiftfox 2.0 with Dapper).

Any alternative solutions?

---

### Post by dushkal on 2007-01-29
Hi,

I'm not sure if this is too late (the thread is more than a month old...) but installing the locale files help in this case. firefox script checks in  /var/lib/locales/supported.d/ if the locale is supported or not and then sets the MOZ_DISABLE_PANGO So, adding the locale in the supported list would enable the support here....

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

---

### Post by akwatve on 2007-12-04
Dushkal,

I am not sure what do you mean in the previous post. I do not have any code in my /usr/bin/firefox that sets or unsets $MOZ_DISABLE_PANGO. Do you suggest I should inset the code you had posted ? If yes then where ( i mean do I need to put it before or after a particular line or just putting it anywhere in the script will do) ?

Thanks

---

