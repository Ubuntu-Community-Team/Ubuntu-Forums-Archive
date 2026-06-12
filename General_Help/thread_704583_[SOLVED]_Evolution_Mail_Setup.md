---
title: "[SOLVED] Evolution Mail Setup"
date: 2008-02-22
forum: General Help
---

### Post by foosed on 2008-02-22
I have been trying to set up a university webmail account to work with evolution and have been unsuccessful. All I have to go on about the university's server information are these two tutorials for setting up outlook and thunderbird, found here:
[http://www.circa.ufl.edu/cd-rom/version8/email/outlook2007.htm](http://www.circa.ufl.edu/cd-rom/version8/email/outlook2007.htm)
[http://www.circa.ufl.edu/cd-rom/version8/email/thunderbird.htm#mail](http://www.circa.ufl.edu/cd-rom/version8/email/thunderbird.htm#mail)
I have tried to adapt both of these to evolution as best I could, but it hasn't been able to connect to the imap or smtp servers. I have the incoming server as imap.ufl.edu with no encryption, outgoing set to smtp.ufl.edu with tls encryption and authentication method set to login. passwords and username have been checked and rechecked. if anyone can figure out what I have done wrong, I would greatly appreciate it.

---

### Post by cmnorton on 2008-02-22
What are the errors?

I have been running Evolution, first as a POP3 client against Mercury and now against World Client running IMAP with POP3 disabled. How Evolution behaves connecting to an IMAP server is another subject, but I can send and receive email. World Client is a web-based mail server.

Does your web mail service require authentication for sending? It might; ours doesn't. So, for example, if I were to configure Evolution to require outbound authentication when it is not required my outbound mail would fail.

I have to believe your server would require inbound mail authentication. You'll need to know those rules, as well. Is the authentication encrypted, for example?

You might be able to test this by telneting to the server on port 143 just to see if the server answers. You could also check to see if your firewall is operational on the client where Evolution is installed.

---

### Post by foosed on 2008-02-22
I don't get any specific errors, when I click send receive a pop up come up and goes away too fast for me to read it, and no mail is retrieved. (there is definitely mail in my inbox) As far as I can tell from the tutorials for outlook, the incoming mail is not encrypted but does require password authentication, and outgoing mail has tls encryption.

EDIT: When I tried the "check supported authentication types" again, something new happened. It put a strike through everything except password authentication for IMAP, however it said that the connection to the SMTP server had timed out. When I set up thunderbird It required me to change the default port for the SMTP, I did not see an option to do this in Evolution's setup. Regardless, I can still neither send nor receive mail.

---

### Post by jbaerbock on 2008-02-22
Never tried imap with Evolution but pop3 seems to work fine, maybe might wanna try pop3? Also make sure the right ports are set. Thunderbird has a spot to set this under account properties but in Evolution just type :578 or whatever port it is after the imap.whatever.com.

For example for me outgoing server looks like this:

smtp.aol.com:587  

AOL smtp uses a special port compared to most email servers so therefore it is necessary to add the :587 at the end to indicate the port. Could this be a similar problem on your end with your university ports?

---

### Post by jbaerbock on 2008-02-22
From what I read on your links it does look like smtp uses 587 for a port so make sure to make your outgoing server smtp.ufl.edu:587

From what I can tell the IMAP server uses default ports though so should be fine there.

---

### Post by foosed on 2008-02-22
Thanks, adding the :587 allows me now to send email, however I am still not receiving. I added :143 to the IMAP server even though that should be default like you say, but still no incoming.

---

### Post by dcstar on 2008-02-23
> **foosed said:**
> Thanks, adding the :587 allows me now to send email, however I am still not receiving. I added :143 to the IMAP server even though that should be default like you say, but still no incoming.

IMAP does not "receive", the e-mails are on the server and you have to expand the folders for that account and then select each e-mail listed to have them downloaded.

There will be an additional Inbox on your system, look in it.

---

### Post by foosed on 2008-02-23
wow, I feel stupid now. Yep they're there, I just saw inbox under the "on this computer" and assumed that was it. Alirght, well everything's working now, thanks everyone for the help.

---

