---
title: "Help running Eclipse on KDE"
date: 2007-02-03
forum: General Help
---

### Post by tyler_roach on 2007-02-03
Hi,

I'm trying  to run the Eclipse IDE on my system,  but it won't start. When I  run  "eclipse" from the command line, I get the following message:

```
searching for compatible vm...
  testing /usr/lib/jvm/java-gcj...found
kdialog: Unknown option '--warning'.
kdialog: Use --help to get a list of available command line options.
```

Does anyone know what is causing this or how it can be fixed? Does Eclipse not work in KDE?

Thanks

---

### Post by phossal on 2007-02-03
You need a suitable JDK (Java Development Kit). Download it from SUN. You can use the tutorial in my sig, or I can walk you through it.

[edit] If you're serious about working with eclipse, I recommend downloading the JDK directly from SUN, and eclipse from eclipse.org. However, if you're in a crunch and need to get going, you can download a backports package of the JDK like this:
```
sudo apt-get install sun-java6-jdk
```
I don't like that method for a variety of reasons, but it's *simple* and requires very little understanding of anything. lol

---

### Post by tyler_roach on 2007-02-03
I did install Java 5.0

sudo aptitude install sun-java5-jdk

I couldn't find Java6 in the repositories.

I understood from the message:

searching for compatible vm...
  testing /usr/lib/jvm/java-gcj...found

That eclipse could find the installed Java.

I'll try your tutorial when I have some free time, but any advice about fixing the current problem?

Thanks

---

### Post by phossal on 2007-02-03
Yes. Find out where the JDK is installed. For example, run:
```
sudo update-alternatives --config java
```
And make sure you're running the latest Java.

Try: 
```
locate javac
```

If you know where the *javac* command is, you can set the path: /PATH_TO_JDK/bin which is what eclipse is looking for.

[EDIT] I'm guessing your fix is this easy:
```
gedit ~./bashrc
```

```
[COLOR="Gray"][SIZE="1"]#BEG Copy and Paste 
#Copy and Paste at the bottom of your .bashrc file 
# ~~~~~~~~~~~~~~~~~ JAVA (JDK,JRE) ~~~~~~~~~~~~~~~~~~~~~ [/SIZE][/COLOR]
export JAVA_HOME='/usr/lib/jvm/java-1.5.0-sun' 
PATH=$PATH:$JAVA_HOME:$JAVA_HOME/bin:$JAVA_HOME/jre/bin
[COLOR="Gray"][SIZE="1"]# 
# The eclipse alias below assumes that you have extracted the eclipse folder 
# to your desktop. It can be anywhere. Edit path as necessary 
# alias eclipse='java -jar /home/<user>/Desktop/eclipse/startup.jar' 
#END Copy and Paste[/SIZE][/COLOR]
```
```

source ~/.bashrc
```

---

### Post by phossal on 2007-02-03
> **tyler_roach said:**
> I did install Java 5.0 
sudo aptitude install sun-java5-jdk
I couldn't find Java6 in the repositories.

5.0 is fine. You couldn't find sun-java6-jdk because you have to *enable* the backport repository. It's a package provided by a 3rd party.

> **tyler_roach said:**
> 
I understood from the message:
searching for compatible vm...
  testing /usr/lib/jvm/java-gcj...found
That eclipse could find the installed Java.

Yes, it's finding the *default* version of Java installed in Ubuntu. That doesn't work with eclipse. That error message is saying that it's found the base install of gcj, which **isn't** related to your Java 5 JDK

> **tyler_roach said:**
> I'll try your tutorial when I have some free time, but any advice about fixing the current problem?
See my previous post.

---

### Post by tyler_roach on 2007-02-03
I got it:

When eclipse starts up, it looks for Mozilla SWT binding, thus:

```
# Set path for the Mozilla SWT binding
MOZILLA_FIVE_HOME=${MOZILLA_FIVE_HOME%*/}
if [ -n "$MOZILLA_FIVE_HOME" -a -e $MOZILLA_FIVE_HOME/libgtkembedmoz.so ]; then
    :
elif [ -e /usr/lib/firefox/libgtkembedmoz.so ]; then
    export MOZILLA_FIVE_HOME=/usr/lib/firefox
elif [ -e /usr/lib/firefox/libgtkembedmoz.so ]; then
    export MOZILLA_FIVE_HOME=/usr/lib/firefox
elif [ -e /usr/lib/xulrunner/libgtkembedmoz.so ]; then
    export MOZILLA_FIVE_HOME=/usr/lib/firefox
elif [ -e /usr/lib/mozilla-firefox/libgtkembedmoz.so ]; then
    export MOZILLA_FIVE_HOME=/usr/lib/mozilla-firefox
elif [ -e /usr/lib/mozilla/libgtkembedmoz.so ]; then
    export MOZILLA_FIVE_HOME=/usr/lib/mozilla
else
    $DIALOG \
        --warning \
        --title="Integrated browser support not working" \
        --text="This Eclipse build doesn't have support for the integrated browser."
    [ $? -eq 0 ] || exit 1
fi

# libraries from the mozilla choosen take precedence
LD_LIBRARY_PATH=$MOZILLA_FIVE_HOME${LD_LIBRARY_PATH:+:$LD_LIBRARY_PATH}
```

However, I don't have Firefox or Mozilla, so it attemped to give me the error message: "--warning," etc. Kdialog doesn't recognize the command "--warning," therefore the failure to start up.

An ideal solution would have been to translate the "--warning" bit into something kdialog understands, eg "--warningcontinuecancel" or "--error." But since I haven't figured out exactly how to do that yet, I just commented out the whole flippin section, and voila -- it starts.

Thanks for the advice phossal, and I'll check your tutorial and make sure eclipse is using the most recent Java.

---

### Post by phossal on 2007-02-03
I have the eclipse startup script posted as an example for a similar problem in the tutorial. I'm not sure how you *got* eclipse, but the startup script is just one of three ways it can be launched. You can also use the in-file executable, and the jar file. 

Interesting example though, I've yet to see that section of the script fail. Interesting that it wasn't echoing that error message. 

Anyway, congrats on getting up and running.

---

### Post by tyler_roach on 2007-02-03
[Thanks. I got eclipse from aptitude.

---

