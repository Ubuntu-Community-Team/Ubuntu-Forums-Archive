---
title: "Thunderbird fails to get gmail messages using pop3"
date: 2022-04-30
forum: General Help
---

### Post by Robbyx on 2022-04-30
I  cannot get any new emails into TB. The sticking point is when I click to get the pop3 email, a window opens at accounts.google.com requiring me to enter credentials for my Google name. Entering  my email address is ignored, as is my phone number. I have been into the google account via Firefox with no problem.  

In  TB I have allowed cookies, because some suggest that is the cause.

Has anyone ideas what I can do?

---

### Post by ajgreeny on 2022-04-30
Is this a new problem just started or have you had it for some time?

I assume you are aware that google have said that T'bird is an insecure application and you have to accept that in their settings.  I am often getting email queries from google asking me to confirm that I wish to continue with T'bird as I often run new OSs as a virtual machine and google immediately sees this as a new device that is trying to access my gmail account.

Have you changed  T'bird's Account Settings -> Server Settings ->  Authentication Method  to ***OAuth2*** in T'bird's Account Settings, which I believe is needed now for successful connection.

---

### Post by Robbyx on 2022-04-30
TB got corrupted at the end of last week. Emails saved into TB were showing the wrong text content or empty.  I do not know why. After trying different ideas including restoring from the backup, I reinstalled Ubuntu 20.04 and restored   TB  in the clean install. It did not  make much difference if any.

In trying to get the pop3 and smtp to work as it always has, I did change the authentication method but the sticking point still remains.

I am using Ubuntu not Lubuntu  as in the first posting's Header.

---

### Post by Robbyx on 2022-04-30
I do not know actually why I have it working now. TB has just downloaded 260 messages.

The change came when I decided to log in to my google account via Firefox. I had done this many times since the crash.  A notification arose asking if I wish to allow TB to access the account. I agreed, went to TB and was able to d/L. 

This is the first time I was able to approve TB to access the account. I guess that it worked because 

1. TB was in the background trying to access the account..
2. The page I was seeing when TB wanted access was not FF but TB

---

### Post by ajgreeny on 2022-05-01
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to other users searching the forum.

---

