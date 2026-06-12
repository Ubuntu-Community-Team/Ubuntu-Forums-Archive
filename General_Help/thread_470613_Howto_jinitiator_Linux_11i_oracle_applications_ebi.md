---
title: "Howto jinitiator Linux 11i oracle applications ebiz"
date: 2007-06-11
forum: General Help
---

### Post by graved on 2007-06-11
I know that there are a couple of pages out there on this, but with Feisty jinitiator seems to be easy to install.  I don't fully understand this stuff, but this seems to work on my newly installed 7.04 ubuntu.  I know that this is the long way around, but you know how it is trying to reconstruct the steps that you took after the fact and I'm trying to make it easy for those that don't understand all the steps (like myself).  Feel free to clarify or comment.

This takes 2 minutes to do.
-David


1:  Server Side:
# Get your sun_plugin_ver from $CONTEXT on the oracle ebiz / 11i application server
applmgr@sspr014$ grep sun_plugin_ver /u01/app/applmgr/OAPRD/admin/OAPRD_s05703.xml
         <sun_plugin_ver oa_var="s_sun_plugin_ver">1.4.2_04</sun_plugin_ver>

# <<< My version is 1.4.2_04 >>>


2:  Client Side (Ubuntu for me):
1. Start firefox
   URL:  about:plugins  (Type this in to the URL / address field of firefox)
   Make mental note of amount of lines in the java plugin section.  (This section is FYI and you could skip it)

2. Exit firefox (Stop all instances of firefox)
   cd $HOME/.mozilla/firefox (Or wherever yours is)
   cp -p pluginreg.dat  pluginreg.dat.before_jinit

3. Install java and plugin
   sudo apt-get install  sun-java5-plugin sun-java5-jre  (This version works for me and that's all that i need.)

4. Start / stop (probably not necessary, but won't kill you to do)
   Start Mozilla
   Exit Firefox (exit all instances of firefox)

5. Backup / modify pluginreg.dat file.
   cd $HOME/.mozilla/firefox  # find your pluginreg.dat file's directory.
   cp  pluginreg.dat  pluginreg.dat.before_jinit

   # Search for a line like the following and modify the version to be the version found above on your server.  (search for jpi)
15:application/x-java-applet;jpi-version=1.4.2_04:Java::$

6. restart firefox.
   Check the plugins for new entries:
    URL:  about:plugins  (Type this in to the URL / address field of firefox) (This section is FYI and you could skip it)

7. Connect to oracle applications
   Make sure that you allow popups for your server(s) and it should work.

Hope this works for you.  The keys is getting the correct version of java on your machine and matching the line above with the version from your context on the Oracle Financials / Applications server.  Please reply if it works, I've been searching for months for an easy way to do this and it would be cool to know if it works for others -- or not ;-(   .

-David

---

### Post by GerryGG on 2008-01-28
David,

Thank you for posting this Howto. I was able to get Jinit to work using your instructions (I'm running Ubuntu 7.10). Initially I had some trouble finding the right java plugin version number, but then I found it by right clicking on the non-functioning form (webpage), and then on "View Page Source". And, within the html code, I was able to locate the version number. I simply amended the pluginreg.dat file as you had suggested. (Actually, I did it a little bit differently. Another Howto suggested to add a new line to the pluginreg.dat with the applicable version number, and then increasing the line count found at the top of the java plugin section.) And, it worked. Thank you very much.

I don't understand oracle or java much at all, and my understanding of html is somewhat limited. But, it seems odd that there are all these forms in use on webpages that require the use of an obscure version of Java. Clearly, the form doesn't require the version it says it does, as the workaround that David had suggested is to trick the form into "thinking" that the specific java plugin version asked for on the form is present, when in fact it is not. Right? So, there's got to be a better way to program these forms. (And, incidentally, this doesnt appear to be a weakness with Ubuntu or linux per se. My XP box couldn't find the right plugin either.)

---

### Post by Niels Olson on 2008-06-18
This worked for me also, but I my firefox was using another pluginreg.dat, in a subdirectory, ~/.mozilla/firefox/vkuuxfit.default/pluginreg.dat. Once I edited the main one, it didn't take so I did a locate for the file. The two are identical, I kind of wonder why it isn't a symlink. There's yet another copy, ~/.mozilla/pluginreg.dat, but it didn't look the same and I didn't have to change it.

---

