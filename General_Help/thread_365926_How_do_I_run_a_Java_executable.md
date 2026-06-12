---
title: "How do I run a Java executable?"
date: 2007-02-20
forum: General Help
---

### Post by Trumpet675 on 2007-02-20
I am trying to execute an executable file called RadRails on my newly installed Edgy release but I keep getting the following error:

bash: ./RadRails: No such file or directory

I am told that it is a Java executable and I have installed the latest Java RE from Sun as perscribed in the Ubuntu desktop guide.

I have checked file permissions and they are fine.

It runs on Ubuntu 6.06 Dapper.

fyi, I am running an AMD64 machine.

Any thoughts appreciated.

---

### Post by Ramses de Norre on 2007-02-20
If it's a java executable it should be a .class or .jar file.
The first can be ran with **java ClassName** (so without the .class extension).
The second with **java -jar file.jar**.

---

### Post by Trumpet675 on 2007-02-20
thanks. The file has no extension so maybe I am wrong and it isn't java.

The File Browser tells me that it is of type "application/x-executable" and the installation guide for the software states that it can be run by:

./radrails/RadRails where radrails is the directory created when the tar file is unpacked.

I can run it in this way on Dapper.

---

### Post by Ramses de Norre on 2007-02-20
Then it isn't a java executable..
Are you sure you're in the right directory when you get that file not found error? Use tab completion to be sure.

---

### Post by Trumpet675 on 2007-02-20
The software is an IDE built on Eclipse and hence this is why I assumed it was Java.

What is tab completion?

I have tried issuing './RadRails' in the directory itself and still get the message.

I can for example execute 'ls RadRails'

---

