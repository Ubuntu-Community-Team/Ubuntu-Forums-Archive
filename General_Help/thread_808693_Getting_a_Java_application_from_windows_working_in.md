---
title: "Getting a Java application from windows working in Xubuntu"
date: 2008-05-26
forum: General Help
---

### Post by AustinMatherne on 2008-05-26
I'm trying to get Fujitsu xwand to work in Xubuntu.

It's a Java application thats normally launched from a batch file in windows.

here's the code from the batch file.

```
java -mx800m -ms256m -classpath lib\instancecreator2.jar;lib\tool-common.jar;lib\taxeditor2.jar;lib\xwexplore.jar;lib\xwandlink.jar;lib\xmlpro.jar;lib\xmlschemac.jar;lib\xmltransx.jar;lib\xwand.jar;lib\xwandschema.jar;lib\xbrldiff2se.jar -Dcom.fujitsu.xml.xbrl.report.taxonomy.supportCSV=yes com.fujitsu.xml.xbrl.xwexplore.XWandExplorePlatform %*


```

Running the above in the same directory as the batch file, but from the command line gets me this.

```
bash: libtool-common.jar: command not found
bash: libtaxeditor2.jar: command not found
bash: libxwexplore.jar: command not found
bash: libxwandlink.jar: command not found
bash: libxmlpro.jar: command not found
bash: libxmlschemac.jar: command not found
bash: libxmltransx.jar: command not found
bash: libxwand.jar: command not found
bash: libxwandschema.jar: command not found
bash: libxbrldiff2se.jar: command not found

```

If I change the code from the command line to this (changing the \ to /).

```
java -mx800m -ms256m -classpath lib/instancecreator2.jar;lib/tool-common.jar;lib/taxeditor2.jar;lib/xwexplore.jar;lib/xwandlink.jar;lib/xmlpro.jar;lib/xmlschemac.jar;lib/xmltransx.jar;lib/xwand.jar;lib/xwandschema.jar;lib/xbrldiff2se.jar -Dcom.fujitsu.xml.xbrl.report.taxonomy.supportCSV=yes com.fujitsu.xml.xbrl.xwexplore.XWandExplorePlatform %*


```

I get this.

```
bash: lib/tool-common.jar: Permission denied
bash: lib/taxeditor2.jar: Permission denied
bash: lib/xwexplore.jar: Permission denied
bash: lib/xwandlink.jar: Permission denied
bash: lib/xmlpro.jar: Permission denied
bash: lib/xmlschemac.jar: Permission denied
bash: lib/xmltransx.jar: Permission denied
bash: lib/xwand.jar: Permission denied
bash: lib/xwandschema.jar: Permission denied
bash: lib/xbrldiff2se.jar: Permission denied

```

Using sudo doesn't help ether.

I need this for work and I'd rather not have to install Windows for this one application.

I've uploaded the program [here]("http://dl4u.savefile.com/dd8f79f3b5290747f63acb64df89cb6c/biz21_46.7z") (9.6 MB) if someone wants to take a look.

Thanks,
~ Austin

---

### Post by diaa on 2008-05-26
What about 
```

java -mx800m -ms256m -classpath lib/instancecreator2.jar:lib/tool-common.jar:lib/taxeditor2.jar:lib/xwexplore.jar:lib/xwandlink.jar:lib/xmlpro.jar:lib/xmlschemac.jar:lib/xmltransx.jar:lib/xwand.jar:lib/xwandschema.jar:lib/xbrldiff2se.jar -Dcom.fujitsu.xml.xbrl.report.taxonomy.supportCSV=yes com.fujitsu.xml.xbrl.xwexplore.XWandExplorePlatform %*
```

It works well for me, the only difference is replacing semi-colons with colons because that's the standard path list separator in Linux, unlike Windows where it is a semi-colon.

Enjoy :)

---

### Post by AustinMatherne on 2008-05-26
Works perfectly, thank you!

~ Austin

---

