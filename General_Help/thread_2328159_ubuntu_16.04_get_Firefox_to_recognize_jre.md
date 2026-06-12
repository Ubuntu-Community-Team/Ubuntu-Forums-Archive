---
title: "ubuntu 16.04 get Firefox to recognize jre"
date: 2016-06-17
forum: General Help
---

### Post by Sherman_Willden on 2016-06-17
If this a faq question? If so please ignore.

When I perform 'http://java.com/en/download/testjava.jsp' and received the following: We are unable to verify if Java is currently installed and enabled in your browser.

So how do I get Firefox to recognize java. I assume it is the jre that I am looking for.

Thank you;

Sherman

---

### Post by QIII on 2016-06-17
Hello!

Have you installed Java?

---

### Post by Sherman_Willden on 2016-06-17
Yes. Java 8 jdk is installed. I have Netbeans installed and working.

---

### Post by QIII on 2016-06-17
How did you install it?

---

### Post by Sherman_Willden on 2016-06-17
Through apt-get. Is there a way to show apt-get history?

---

### Post by Sherman_Willden on 2016-06-17
I searched faq's for 'Firefox java' and 'Firefox jre' without success

---

### Post by &amp;KyT$0P# on 2016-06-17
> **Sherman_Willden said:**
> Is there a way to show apt-get history?
Look at /var/log/apt/history.log (or the appropriate history.log*.gz file in /var/log/apt)

---

