---
title: "lightdm setup script sed not working"
date: 2016-09-05
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2016-09-05
I have a lightdm setup script 
```
greeter-setup-script=/usr/local/bin/greeter-setup-script
```
```
#!/bin/bash
numlockx on
if [ $(date +%H) -lt 9 ];then
    /usr/local/bin/backlightx --set 50 > /var/log/backlightx_debug
elif [ -f /var/log/backlightx ];then
    val=$(cat /var/log/backlightx)
    if [ ${#val} -gt 0 ];then
        backlightx --set $val
    fi
fi
#ogg123 /usr/share/sounds/ubuntu/stereo/system-ready.ogg &
exit

```
in my backlightx script i use sed to validate input data
this line returns true when echo $2 returns 50
```
if [ ! "$(sed 's/[a-Z]//g' <<< $2)" == "$2" ];then
```
this should only return true if there is a letter in $2
even if i change $2 to a 50 it still returns true as sed returns a empty string
of course this command works just fine and sed returns the number 50 like it should
```
sudo -u lightdm backlightx --set 50
```

in case you are not sure what i am saying if i put this in my backlightx script 
```
echo $(sed 's/[a-Z]//g' <<< 50)
```
it does the same same as [FONT=Courier New]echo ""[/FONT] but only when run from the setup script

---

### Post by steeldriver on 2016-09-05
How did you determine that sed is returning an empty string? Are you saying that `s/[a-Z]//g' is replacing digits as well as alphabetics? if so, then the only thing I can think of is that there is some kind of weird collation order in effect

In any case, things like [a-z], [A-Z], [a-Z] are inherently susceptible to weird (locale-dependent) results. Also there's really no need to use sed here: some (IMHO) better options would be either to use a case statement

```

case "$2" in 
  *[[:alpha:]]*) echo "contains alpha"
  ;; 
  *) echo "OK"
  ;; 
esac

```

or make use of bash's built-in regular expression testing (note that this requires the [[ .. ]] extended test in place of  [ .. ] )

```

if [[ $2 =~ [^[:digit:]] ]]; then
  echo "contains non-digit"
fi

```

---

### Post by Keith_Helms on 2016-09-05
I've always seen [a-zA-Z] used for letters.  A capital Z has a lower ascii value (x'5A') than a lowercase a (x'61'), so [a-Z] doesn't make sense.

---

### Post by pqwoerituytrueiwoq on 2016-09-05
> **steeldriver said:**
> ```

if [[ $2 =~ [^[:digit:]] ]]; then
  echo "contains non-digit"
fi

```

i like that way more and it works
edit:
 [a-zA-Z] does work also

---

