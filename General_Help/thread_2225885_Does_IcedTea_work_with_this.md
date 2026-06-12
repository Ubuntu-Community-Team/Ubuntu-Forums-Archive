---
title: "Does IcedTea work with this?"
date: 2014-05-24
forum: General Help
---

### Post by NoBugs! on 2014-05-24
Anyone have luck on this website, with the Icedtea Java plugin?

[http://www.mambosprouts.com/coupon-gallery](http://www.mambosprouts.com/coupon-gallery)

It's just showing a grey box for me, and not printing, though Java test site shows Java 7 plugin enabled.

Looks like this may be a cause of faiure, in the log:

plugin_send_message_to_appletviewer
  PIPE: plugin wrote(?): plugin PluginCookieInfo reference 10 
plugin_send_message_to_appletviewer return
plugin_in_pipe_callback return
java.lang.ClassNotFoundException: com.itextpdf.license.LicenseKey
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.loadClassExt(JNLPClassLoader.java:1692)
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.loadClass(JNLPClassLoader.java:1492)
	at java.lang.Class.forName0(Native Method)
	at java.lang.Class.forName(Class.java:190)
	at com.itextpdf.text.Version.getInstance(Version.java:96)
	at com.itextpdf.text.pdf.PdfDocument$PdfInfo.addProducer(PdfDocument.java:168)
	at com.itextpdf.text.pdf.PdfDocument$PdfInfo.<init>(PdfDocument.java:94)
	at com.itextpdf.text.pdf.PdfDocument.<init>(PdfDocument.java:1679)
	at com.itextpdf.text.pdf.PdfWriter.getInstance(PdfWriter.java:610)
	at QplesPrinter.start(QplesPrinter.java:1007)
	at sun.applet.AppletPanel.run(AppletPanel.java:476)
	at java.lang.Thread.run(Thread.java:744)

---

### Post by LastDino on 2014-05-24
[ATTACH=CONFIG]253410[/ATTACH]

Is that it? 
I never install any java plug-in on my browser as far as I can tell. It seems to be working for me without any java anyway.

---

### Post by NoBugs! on 2014-05-24
So you were able to "clip" and print the coupons? How?

Seems other sites use this Qples coupon system - Zevia soda for example. Surely someone's set it up with Linux?

---

### Post by monkeybrain20122 on 2014-05-24
I can see the page, I am able to clip, not sure about printing because a popup says you have to like it on facebook to print. I stopped right there. I don't even have java activated.

---

### Post by LastDino on 2014-05-24
> **monkeybrain20122 said:**
> I can see the page, I am able to clip, not sure about printing because a popup says you have to like it on facebook to print. I stopped right there. I don't even have java activated.

+1 I stopped here as well, I don't like anything on internet needing me to associate with something as personal as facebook with.

---

### Post by NoBugs! on 2014-06-02
Weird, I never saw that screen. Are you sure you didn't click "share coupon" instead of "print coupon"? Maybe that pops up after the Java initialization that isn't running on mine for some reason?

---

### Post by monkeybrain20122 on 2014-06-02
We told you that we don't even have java.

---

