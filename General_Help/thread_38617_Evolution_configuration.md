---
title: "Evolution configuration"
date: 2005-06-01
forum: General Help
---

### Post by amazinmic on 2005-06-01
Hello,

Having trouble configuring my evolution to see my Exchange Server. The problem in particular is a setting reffering to OWA (Outlook Web Access). Can anyone explain why I need to authenticate using this, or am I doing something wrong?

Thanks

---

### Post by tristesse on 2005-06-02
I have the same problem configuring Evolution to see our Exchange Server.   I add a valid username, insert the appropriate OWA Url, and authenticate with the correct password, but the following error occurs:

"Could not configure Exchange account because an unknown error occurred.  Check the URL, username, and passsword, and try again."

I am new to Ubuntu, so would appreciate some advice.

---

### Post by falconsclaw on 2005-06-03
I got it working, mostly, by two ways.  The OWA URL: field was given:

http://servername/exchange

The Username field was given my domain username without domain info ("DOMAIN\" or "@domain").  I clicked authenticate and gave my password and that worked.  I can see all my mailbox folders, and send and receive mail.  However, in trying to get Public Folders working somehow, I reconfigured my mail account. This caused an error stating it can't find the file.  I then changed the "OWA URL:" field to read:

http://servername

This removed the error and I am back to seeing my mailbox folders and sending and receiving mail.  Now why *both* configurations worked, I don't know.  But I still have no access to Public Folders other than viewing the list under the "Exchange" button.

I'm going to blow away the account profile completely and retry with just the "http://servername" from the start.  My thinking is that OWA refers to your mailbox under "/exchange" and Public Folders under "/public".  I think the connector can/should figure that out from the root of that web URL.  If anyone has more or corrected info on this, please let me know.  I'll post the results after I re-create the account.

---

### Post by falconsclaw on 2005-06-03
Ok, that didn't take long.  I removed the email profile and restarted Evolution.  I then recreated as I described above, with only "http://servername" as the OWA URL field.  The username was done as before.  Authenticate and complete the wizard.  Now I get a new folder at the top level under the account called "Favorite Public Folders".  I can now add Public Folders to this list.  I still can't seem to traverse the folders (which would be nice).  Well, I'm farther along now and I'll keep plugging.  Hope this helps a little...

---

