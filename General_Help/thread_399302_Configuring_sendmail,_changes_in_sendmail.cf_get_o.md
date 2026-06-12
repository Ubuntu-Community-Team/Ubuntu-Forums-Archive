---
title: "Configuring sendmail, changes in sendmail.cf get overwritten on reboot"
date: 2007-04-02
forum: General Help
---

### Post by azzid on 2007-04-02
Hi,

I've been spending some time trying to make sendmail able to handle the swedish characters å ä ö in a good way.

I just found the setting 

# default character set
#O DefaultCharSet=unknown-8bit

in sendmail.cf, changing it into

# default character set
O DefaultCharSet=ISO-8859-1

does the trick. However, when I reboot the sendmail.cf is regenerated from,  among others, the file sendmail.mc. How can I add the desired setting to the mc-file?

I also uncommented the following

# 8-bit data handling
#O EightBitMode=pass8

when I got it to work, but that setting get overwritten as well, how can I specify that in the mc-file?

---

### Post by azzid on 2007-04-02
[This german page]("http://freenet-homepage.de/slgig/cfreadme_de/tweaking_config.html") helped me understand that the line I needed in my mc-file was:

define(`confDEF_CHAR_SET', `ISO-8859-1')

after adding that and running sendmailconfig my sendmail.cf now looks the way I want it. Atleast the DefaultCharSet line.

---

