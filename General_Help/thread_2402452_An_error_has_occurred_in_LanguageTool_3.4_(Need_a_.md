---
title: "An error has occurred in LanguageTool 3.4 (Need a JAVA expert)"
date: 2018-09-30
forum: General Help
---

### Post by cigtoxdoc on 2018-09-30
How does one deal with the error shown below?

An error has occurred in Language-Tool 3.4:
java.lang.lloClassDefFoundError: javaxJ'xm|J'hind1]AXI!Exceptia-n Stacktrace:
 java.|ang.HoC|assDefFoundError:javax!:Itm|IhindI]AXI!Exception 
at net.Ia-omchild.segment.srx.in-.Srx2SaxParser.<init>(Sn(2SaxParser.java:l73} 
at org.|anguagetool.tokenizers.SrxToo|s.createSrxDocu ment(5rxTools.java:51) 
at org.languagetool.tokenizers.5RXSentence‘I'okenizer.<init:=- [S IlX5entenceTokenizer.java:53} 
at org.Ianguagetool.tokenizers.Simplesenten-ceTokenizer.<init>(Simp|eSentenceTo|(enizer.java:37) 
at org.|anguagetool.Language.-::c|init>(Language.java:60} at java.haseljava.|ang.C|ass.forHame0(Native Method} 
at java.haseJjava.lang.C|ass.forHame(C|ass.java:29l) 
at org.languagetool.Languages.createLanguage{)bjects(Languages.java:111) 
at org.languagetool.Languages.getA|ILanguages(l.anguages.java:97} 
at org.|anguagetaol.Languag-es.<c|init>(Languages.java:39) at org.|anguagetool.openn-ffice.Main.getLoca|es(Main.java:543} 
Caused by: java.lang.ClassNotFoundException: javax.xm|.hind.]AXBException 
at java.haseJjava.net. llIlLC|assLoader.findClass(U RLClassLoader.java:466) 
at java.haseJjava.|ang.C|assLoader.loadc|ass(C|assLoader.java:566} 
at java.baseljava.lang.Classloader.loadclasslclassloade.-r.java:499I 11 more 
05: Linux on amdfill, Java version 10.0.2 from Oracle Corporation

Error shown above occurs each time LibreOffice Writer is opened.  LanguageTool is mission critical

All software has been updated.  This error started on 27 or 28 September.

John

---

### Post by Holger_Gehrke on 2018-09-30
That error message is close to unreadable. What did you do, take a picture with your phone and run it through OCR ?

Two things: 
LanguageTool is available in Version 4.3 from [https://extensions.libreoffice.org/extensions/languagetool](https://extensions.libreoffice.org/extensions/languagetool) . Unless the version number at the beginning of the message is completely wrong, you're using a version from June 2016. 
And when I tried a current version of LanguageTool with LibreOffice 6.0.6 on XUbuntu 18.04, it did not work with Java 10. It doesn't work completely right with Java 8 either (clicking on the "Help" button next to either path entry field on the first tab of the Options dialog will crash libreoffice with a message about using both gtk+ 2 and gtk+ 3 in the same process not being supported), but it does work.

Holger

---

### Post by cigtoxdoc on 2018-09-30
Holger, thank you very much for your message.  Problem solved following your suggestion to upgrade to Version 4.3 of LanguageTool.  I am using version 11 of the java from java-11-openjdk-amd64.  Libreoffice reports this Oracle Corporation 10.0.2.  Libreoffice writer is 6.0.6.2.

John

---

