---
title: "Using Java send mail not work on ubuntu"
date: 2007-01-24
forum: General Help
---

### Post by moonhk on 2007-01-24
I have following API. I want test sent mail in ubuntu. It is ok on solaris and Window.

CLASSPATH=/home/moonhk/javaux:/mnt/disk2/Example/java/api/javamail-1.3.2/mail.jar:/mnt/disk2/Example/java/api/jaf-1.0.2/activation.jar

Compile program ok
moonhk@hex:~/javaux/mail$ javac exmail.java
moonhk@hex:~/javaux/mail$

Where /usr/lib/jvm/java-gcj/jre/bin/java
Where /usr/lib/jvm/java-1.5.0-sun/bin/javac

Is java-gcj not ok ? I already add Sun Runtime.It still  using java-gcj.

Run is not ok

moonhk@hex:~/javaux/mail$ java exmail
Exception in thread "main" java.lang.NoClassDefFoundError: exmail
   at gnu.java.lang.MainThread.run(libgcj.so.7)
Caused by: java.lang.ClassNotFoundException: exmail not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:/home/moonhk/javaux/,file:/mnt/disk2/Example/java/api/javamail-1.3.2/mail.jar,file:/mnt/disk2/Example/java/api/jaf-1.0.2/activation.jar], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at gnu.java.lang.MainThread.run(libgcj.so.7)
moonhk@hex:~/javaux/mail$


Source code
==========
import java.util.*;
import java.net.*;
// Define java mail import file
// Using Javamail API 1.3
import javax.mail.*;
import javax.mail.internet.*;
import javax.mail.Message.*;

// [http://java.sun.com/products/javabeans/glasgow/jaf.html](http://java.sun.com/products/javabeans/glasgow/jaf.html)
import javax.activation.*;
import javax.activation.FileDataSource;
import javax.activation.DataHandler;

public class exmail {
        public static void main(String[] args){
    

                String host = "210.0.xx.xx";
                String post = "";
                String from = "cxleung@xx.com";
                String to =   "cxleung@xx.com";
                String to1 =   "cxleung@xx.com";
                String passwd = "xxxxxx";

                // Get System properties
                Properties props = System.getProperties();

                props.put("mail.smtp.auth","true");


                // Setup mail server
                System.out.println("Host :=" + host);
                props.put("mail.smtp.host",host);

                // Get Session
                Session session = Session.getDefaultInstance(props,null);
                System.out.println("Define Session - OK");

                // Define message
                try {
                        MimeMessage msg = new MimeMessage(session);
                        System.out.println("Define Message - OK");

                        // set the from Address
                        msg.setFrom(new InternetAddress(from));
                        System.out.println("Set From  - OK");

                        // set the to Address
                        msg.addRecipient(Message.RecipientType.TO,new InternetAddress(to));
                        msg.addRecipient(Message.RecipientType.TO,new InternetAddress(to1));
                        System.out.println("Add Recipient  - OK");

                        // set the subject
                        msg.setSubject("Hello JavaMail by exmail.java");


                        // set the content
                        msg.setText("Welcome to JavaMail");
                        System.out.println("Set Subjust and Text - OK");

                        // send  Message
                        Transport tr = session.getTransport("smtp");
                        tr.connect(host,from,passwd);
                        tr.sendMessage(msg,msg.getAllRecipients());
                        tr.close();

                        System.out.println("Transport - OK");
                }
                catch (Exception e) {
                        System.out.println("error");
                          e.printStackTrace();
                }
        }

}

---

### Post by ebash on 2007-01-24
The problem seems to be with the classpath at run time. In the previous example your classpath includes the folder /home/moonhk/javaux/ but your class in in the folder ~/javaux/mail. To resolve the problem modify your classpath to include the folder which hosts the file exmail.class.

You can invoke the java program with the -classpath option in order to add extra folders to your classpath:

```
java -classpath ".:$CLASSPATH" exmail
```

---

### Post by moonhk on 2007-01-24
You are correct. 

Also, how to add "Code" Box in Message Body ?

moonhk@hex:~/javaux/mail$ java -classpath ".:$CLASSPATH" exmail
Host :=210.0.xxx.xxx
Define Session - OK
Define Message - OK
Set From  - OK
Add Recipient  - OK
Set Subjust and Text - OK
Transport - OK
moonhk@hex:~/javaux/mail$

---

