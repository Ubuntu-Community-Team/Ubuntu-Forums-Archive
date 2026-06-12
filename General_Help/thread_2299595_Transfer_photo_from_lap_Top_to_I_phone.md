---
title: "Transfer photo from lap Top to I phone"
date: 2015-10-19
forum: General Help
---

### Post by gordon33 on 2015-10-19
Hello all

How do you Transfer photo from lap Top to I phone?  I have a photo saved on my lap top that uses Ubuntu 14.04, and I want to send that photo to my I phone 4.

Gordon33

---

### Post by ajgreeny on 2015-10-19
No idea about connecting the two machines by cable but I assume it is possible some way or other.

However, you could just send the photo to yourself as an attachment to an email, or if both phone and laptop are on the same network, use a simple python server just to do the file transfer.

On the laptop use command ```
python -m SimpleHTTPServer 1111
``` then use your web browser on the iPhone to go to the IP address of the laptop using web address, for example [http://192.168.0.10:1111](http://192.168.0.10:1111) (ie, laptop IP address using port 1111) which should then connect to the laptop and allow you to navigate to the photo and download it to phone.

Ctrl+C to stop the server.  Simple but can be effective.

---

