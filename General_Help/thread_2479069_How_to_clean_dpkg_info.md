---
title: "How to clean dpkg info ?"
date: 2022-09-13
forum: General Help
---

### Post by georgesgiralt on 2022-09-13
Hello,
I've just upgraded my laptop to Jammy. It has seen a very long life since it's first Ubuntu installation (around 16.04 LTS.... but was running Ubuntu before that). 
And looking at what Python version I got I see (first 51 lines displayed... )
```

dpkg -l python*
Souhait=inconnU/Installé/suppRimé/Purgé/H=à garder
| État=Non/Installé/fichier-Config/dépaqUeté/échec-conFig/H=semi-installé/W=attend-traitement-déclenchements
|/ Err?=(aucune)/besoin Réinstallation (État,Err: majuscule=mauvais)
||/ Nom                           Version                         Architecture Description
+++-=============================-===============================-============-=============================================================================
un  python                        <aucune>                        <aucune>     (aucune description n'est disponible)
un  python-4suite                 <aucune>                        <aucune>     (aucune description n'est disponible)
un  python-apport                 <aucune>                        <aucune>     (aucune description n'est disponible)
un  python-apsw-doc               <aucune>                        <aucune>     (aucune description n'est disponible)
un  python-apt                    <aucune>                        <aucune>     (aucune description n'est disponible)
ii  python-apt-common             2.3.0ubuntu2.1                  all          Python interface to libapt-pkg (locales)
un  python-apt-doc                <aucune>                        <aucune>     (aucune description n'est disponible)
un  python-aptdaemon-gtk          <aucune>                        <aucune>     (aucune description n'est disponible)
un  python-attr-doc               <aucune>                        <aucune>     (aucune description n'est disponible)
un  python-blinker-doc            <aucune>                        <aucune>     (aucune description n'est disponible)
un  python-boto                   <aucune>                        <aucune>     (aucune description n'est disponible)
un  python-caja                   <aucune>                        <aucune>     (aucune description n'est disponible)
ii  python-caja-common            1.26.0-1                        all          Python binding for Caja components (common files)
un  python-chardet                <aucune>                        <aucune>     (aucune description n'est disponible)
un  python-cryptography-doc       <aucune>                        <aucune>     (aucune description n'est disponible)
un  python-cupshelpers            <aucune>                        <aucune>     (aucune description n'est disponible)
un  python-cycler-doc             <aucune>                        <aucune>     (aucune description n'est disponible)
un  python-dbus-doc               <aucune>                        <aucune>     (aucune description n'est disponible)
un  python-debian                 <aucune>                        <aucune>     (aucune description n'est disponible)
un  python-evdev-doc              <aucune>                        <aucune>     (aucune description n'est disponible)
un  python-future-doc             <aucune>                        <aucune>     (aucune description n'est disponible)
un  python-gdal                   <aucune>                        <aucune>     (aucune description n'est disponible)
ii  python-genshi-doc             0.7.6-1build1                   all          Python XML-based template engine (documentation and examples)
un  python-gi                     <aucune>                        <aucune>     (aucune description n'est disponible)
un  python-gnupg                  <aucune>                        <aucune>     (aucune description n'est disponible)
un  python-httplib2               <aucune>                        <aucune>     (aucune description n'est disponible)
un  python-imaplib2               <aucune>                        <aucune>     (aucune description n'est disponible)
un  python-ipython-doc            <aucune>                        <aucune>     (aucune description n'est disponible)
un  python-lockfile-doc           <aucune>                        <aucune>     (aucune description n'est disponible)
ii  python-lxml-doc               4.8.0-1build1                   all          pythonic binding for the libxml2 and libxslt libraries (documentation)
un  python-mako                   <aucune>                        <aucune>     (aucune description n'est disponible)
un  python-mako-doc               <aucune>                        <aucune>     (aucune description n'est disponible)
un  python-markdown               <aucune>                        <aucune>     (aucune description n'est disponible)
un  python-markdown-doc           <aucune>                        <aucune>     (aucune description n'est disponible)
ii  python-matplotlib-data        3.5.1-2build1                   all          Python based plotting system (data package)
un  python-matplotlib-doc         <aucune>                        <aucune>     (aucune description n'est disponible)
un  python-migrate                <aucune>                        <aucune>     (aucune description n'est disponible)
un  python-minimal                <aucune>                        <aucune>     (aucune description n'est disponible)
un  python-mpmath-doc             <aucune>                        <aucune>     (aucune description n'est disponible)
ii  python-musicbrainzngs-doc     0.7.1-2                         all          Documentation for the Python Musicbrainz NGS interface modules
un  python-mutagen                <aucune>                        <aucune>     (aucune description n'est disponible)
ii  python-mutagen-doc            1.45.1-2                        all          audio metadata editing library - documentation
un  python-mygpoclient            <aucune>                        <aucune>     (aucune description n'est disponible)
un  python-nacl-doc               <aucune>                        <aucune>     (aucune description n'est disponible)
un  python-nautilus               <aucune>                        <aucune>     (aucune description n'est disponible)
un  python-numpy                  <aucune>                        <aucune>     (aucune description n'est disponible)

```
I would like to know how I can clean the packets marked "un" or "rc" ? to reduce the display to a more manageable one ? 
Of course, I _do_ think that Python is just the tip of the iceberg here...
Many thanks in advance for your help !

---

### Post by &amp;KyT$0P# on 2022-09-13
The ones marked "un" are not installed on your system.

To remove the ones marked "rc" I would use Synaptic package manager, where they are listed under "Not installed (residual configuration)".

If you want to list only installed Python related packages, try
```
dpkg-query -l | grep -F -i python
```

---

### Post by georgesgiralt on 2022-09-13
Thank you for your answer. But, how do I clean the tables to have only the one installed listed ? 
I'm not at all interested by the historic of the packages versions.
If I do a dpkg -l query, I get a huge amount of packages marked "un" or "rc".... (for example, the Python packages list is more than 250 lines long.
Edit : I would have used "dpkg-query -l python* | grep ^ii" to find the actual Python packages ;-) Funny as everyone has it's way to solve a problem under Unix/Linux !

---

### Post by #&amp;thj^% on 2022-09-13
With this pattern dpkg-query will **only list installed or configured packages**:
```

dpkg-query -f '${Package}###${Version}\n' -W
```

Moreover, there is no such Python clean state. Each system update and each package you install might bring with it Python related dependencies.

You can however use pip or pip3 to uninstall only packages you previously manually installed and even this is not totally risk free.

Ubuntu relies heavily on different Python versions for functionality. New releases of Ubuntu are slowly shifting to Python3, but older versions of Python are still in use.

You can list some important Ubuntu and Gnome packages on your system that depend on Python3, for example, like so:
```
apt-cache rdepends -i --installed --recurse python3 | \
grep -v " " | sort -u | grep -E "ubuntu|gnome"
```
or on mine I'd use:
```
 apt-cache rdepends -i --installed --recurse python3 | grep -v " " | sort -u | grep -E "debian|xfce4"
xfce4
xfce4-helpers
xfce4-session
xfce4-settings

```

---

### Post by Bashing-om on 2022-09-13
Hello georgesgiralt -

Maybe like so ?

While there is no built in way to remove all of your configuration information from your removed packages you can remove all configuration data from every removed package. To purge all removed but not yet purged packages, where The state is rc, the package is removed, but the config files are not removed....with the following command.
```

dpkg -l | awk '/^rc/{print $2}' | xargs sudo dpkg -P

```

I know of no reason that the same application of "rc" for "un" would not also be effective. However, I have never had an occasion to see.

[INDENT]your testing will be informative[/INDENT]

---

### Post by #&amp;thj^% on 2022-09-13
B-om he should be good to go with your suggestion, Mine to help:
```
 dpkg -l | awk '/^rc/{print $2}' | xargs sudo dpkg -P
[sudo] password for me: 
Sorry, try again.
[sudo] password for me: 
(Reading database ... 544083 files and directories currently installed.)
Purging configuration files for live-tools (1:20190831) ...
Purging configuration files for user-setup (1.89) ...

```

---

### Post by Bashing-om on 2022-09-13
Hey hey 1fallen :D

The "awk '/^rc" string is my goto - have so used it numerous times. Just have not so applied to a "un" state. But "should" workie :D 
However >>
[INDENT]A know it all I am not[/INDENT]

---

### Post by #&amp;thj^% on 2022-09-13
> **Bashing-om said:**
> 
The "awk '/^rc" string is my goto - have so used it numerous times. Just have not so applied to a "un" state. But "should" workie :D 
However >>
[INDENT]A know it all I am not[/INDENT]
+1 Mine as well, I was just concerned the OP was going to nuc his system, trying to remove all the python he showed in post#1
That would have a very un-happy ending...:(

---

### Post by georgesgiralt on 2022-09-14
Hi Guys,
No, I'm not trying to wipe out all the Python packages in my first post...
More than 40 years spent in Unix/Linux server setup and maintenance gave me some refrain....
But since I'm retired, I slowly loose all my knowledge from old age and being far from evolution in software... 
I used Synaptic to clean some "rc" packages. 
And I saw that I had a lot (29) package marked for update which apt update did not touch... And I can't understand why. 
This will wait for another time as retired people are very busy ;-) 
Thanks for your help !
Edit : I selected a couple of them in Synaptic and manually updated them without problems. So it is not a waiting/missing dependency .... 
This update to Jammy had done some strange things.

---

### Post by &amp;KyT$0P# on 2022-09-14
> **georgesgiralt said:**
> And I saw that I had a lot (29) package marked for update which apt update did not touch... And I can't understand why. 

Usually those are phased updates that your system has not been phased into yet.  To see if that's the case, use
```
apt-cache policy [COLOR="#FF0000"]<packagename>[/COLOR]
```
replacing [COLOR="#FF0000"]<packagename>[/COLOR] with the package in question.

---

