---
title: "Is the .mozilla important??"
date: 2005-05-28
forum: General Help
---

### Post by hammett111 on 2005-05-28
When installing the java plugin for mozilla firefox is it important to name the directory ./mozilla? Or is just /mozilla ok??

---

### Post by cinematography on 2005-05-28
If you're using Ubuntu, and all of your files are where they should be, this code should be able to help you install the plugin for java: 


Go to your root terminal and enter the following:
```
cd /usr/lib/mozilla-firefox/plugins
ln -s /usr/java/jre1.5.0_02/plugin/i386/ns7/libjavaplugin_oji.so .
```

---

### Post by hondje on 2005-05-28
[QUOTE=cinematography]If you're using Ubuntu, and all of your files are where they should be, this code should be able to help you install the plugin for java: 


Go to your root terminal and enter the following:
```
cd /usr/lib/mozilla-firefox/plugins
ln -s /usr/java/jre1.5.0_02/plugin/i386/ns7/libjavaplugin_oji.so
```[/QUOTE]

Slight oversight, you forgot the target of the link :)  The second line should look like

```

ln -s /usr/java/jre1.5.0_02/plugin/i386/ns7/libjavaplugin_oji.so .
```

---

### Post by hammett111 on 2005-05-28
Done it, mozilla firefox still crashes on pages that contain Java scripts. When I run firefox from the terminal I get no error outputs.

If I type in "about:plugins" in the firefox browser I get the macromedia falsh plugin and all the MIME scripts, but not the java plugin?

Any hints?

Also my java plugin folder for where the smylink is to is /usr/local/jre1.5.0_01/plugin/i386/ns7 is that okay?

---

### Post by bored2k on 2005-05-28
[QUOTE=hammett111]Done it, mozilla firefox still crashes on pages that contain Java scripts. When I run firefox from the terminal I get no error outputs.

If I type in "about:plugins" in the firefox browser I get the macromedia falsh plugin and all the MIME scripts, but not the java plugin?

Any hints?

Also my java plugin folder for where the smylink is to is /usr/local/jre1.5.0_01/plugin/i386/ns7 is that okay?[/QUOTE]
 Why don't you make your own .deb out of the jre ? and btw, jre has been updated thrice after your version.

---

### Post by cinematography on 2005-05-28
[QUOTE=hondje]Slight oversight, you forgot the target of the link :)  The second line should look like

```

ln -s /usr/java/jre1.5.0_02/plugin/i386/ns7/libjavaplugin_oji.so .
```[/QUOTE]
Hehehe. Don't you just love those tiny little details. Thanks. I updated my post.

---

### Post by hammett111 on 2005-05-28
Gimme a rundown on how to make the deb out of the jre? and truly will this help? I have symlinked to just about everywhere I have the macromedia flash shared library and still no plugin!! God I love this

---

### Post by bored2k on 2005-05-28
[QUOTE=hammett111]Gimme a rundown on how to make the deb out of the jre? and truly will this help? I have symlinked to just about everywhere I have the macromedia flash shared library and still no plugin!! God I love this[/QUOTE]
 I have a .deb file. Backports have a deb file. We all love them :D. They have symlinks :).

1. apt-get build-essential fakeroot java-package java-common
2. fakeroot make-jpkg JAVAFILENAME.bin
3. sudo dpkg -i NEWLYCREATEDjavaFile.deb

---

