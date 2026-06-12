---
title: "Problems with freemind and Java"
date: 2012-11-23
forum: General Help
---

### Post by thorbs on 2012-11-23
I am having problems with java and freeplane. I get the error 

[warning] /usr/bin/freeplane: No java runtime was found
[error] /usr/bin/freeplane: Unable to find an appropriate java runtime. See java_wrappers(7) for help




I am having the openjkd java 6 installed. 

There seems to be a bug and a workaround here

[https://bugs.launchpad.net/ubuntu/+source/java-wrappers/+bug/908679](https://bugs.launchpad.net/ubuntu/+source/java-wrappers/+bug/908679)

But I am not able to actually understand what is written there.


Anybody who can help?

---

### Post by thorbs on 2012-11-23
Found this suggestion to solution in the software center, but do not understand it completely, anybody who can help?


if it does not work try adding JAVA_HOME env var for ex:ive added JAVA_HOME=/usr/lib/jvm/java-7-oracle (yours' might be different!)to /etc/environment then rebooted .

---

### Post by Resistent on 2013-06-11
[SIZE=4]**How it worked:**[/SIZE]

Always, Java applications has to be shown where the folder is where the executable java files are like "java, javac, javaws and so", these are usually in a folder called "/bin" folder. All java applications could have this folder already, with this executable es "java, javac, javaws and so" files.

I just installed freemind with
```
sudo apt-get install freemind
```

Then I get the same problem.
```
[warning] /usr/bin/freemind: No java runtime was found[error] 
/usr/bin/freemind: Unable to find an appropriate java runtime. See java_wrappers(7) for help

```

At first I wanted to change the freemind.sh in the "/usr/bin/ folder. But that's not the true problem. 
```
/usr/bin$ sudo leafpad freemind
```
( Even if you change here the "java6" to "java5" , freemind will also work after the 2 step on the bottom of my post,
but would write many warnings as java version is not the "wanted version 6" )

```
#--------- Put the environment together --------------------------------
_source /etc/freemind/freemindrc
_source ~/.freemind/freemindrc


if [ -r /usr/lib/java-wrappers/java-wrappers.sh ]
then # the Debian method
    . /usr/lib/java-wrappers/java-wrappers.sh
    [COLOR=#0000ff]require_java_runtime[/COLOR] [COLOR=#ff0000]java6[/COLOR]
else
    findjava
    if [ $? -ne 0 ]
    then
        exit 1
    fi
fi
```


**I did 2 things:**

I looked into the folder /usr/lib/jvm, there the folder /bin was empty.
But in /usr/lib/jvm/ there was the subfolder called "java-7-oracle" , and in this one, the /bin folder was filled. So this was the path I needed. /usr/lib/jvm/java-7-oracle/bin

- I changed in /usr/bin/jvm/**jvm-list.sh** the [COLOR=#ff0000][FONT=courier new]__jvm_default="/usr/lib/jvm/default-java"[/FONT][/COLOR] to [COLOR=#ff0000][FONT=courier new]__jvm_default="/usr/lib/jvm/java-7-oracle/bin"
[/FONT][/COLOR]([FONT=arial]/usr/lib/jvm/default-java [/FONT]folder really did not e[FONT=arial]xist, so this was really incorrect path.)[/FONT]
```
/usr/lib/java-wrappers$ sudo leafpad jvm-list.sh
```

- Then I changed in /usr/bin/jvm/**java-wrappers.sh** the[COLOR=#ff0000] [FONT=courier new]DIR=""[/FONT][/COLOR] to [COLOR=#ff0000][FONT=courier new]DIRS="$__jvm_default"[/FONT][/COLOR]
```
/usr/lib/java-wrappers$ sudo leafpad java-wrappers.sh
```

then freemind worked. And, because freemind.sh it was "[COLOR=#0000ff]require_java_runtime [/COLOR][COLOR=#ff0000]java6[/COLOR]", no warnings on the terminal after starting.
(no PC reboot necessary of course)
```
/usr/bin$ freemind 
```


[COLOR=#0000ff]**So to solve the problem, **[/COLOR]

- find the true "[COLOR=#800080]/bin[/COLOR]" folder in in the folder [COLOR=#FF0000][FONT=courier new]/usr/lib [/FONT][/COLOR]where the "java, javaws and so on" files are,  (or find other non-empty java /bin folder)
- correct [COLOR=#FF0000][FONT=courier new]__jvm_default [/FONT][/COLOR]in **jvm-list.sh** to show to this [COLOR=#800080]/bin[/COLOR] path. (in my case it was [FONT=courier new]/usr/lib/jvm/java-7-oracle/bin)[/FONT]
- then use [COLOR=#FF0000][FONT=courier new]__jvm_default [/FONT][/COLOR]in **java-wrappers.sh **as [COLOR=#ff0000]DIRS="$__jvm_default"[/COLOR]

---

