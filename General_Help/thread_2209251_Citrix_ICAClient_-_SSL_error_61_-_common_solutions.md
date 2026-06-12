---
title: "Citrix ICAClient - SSL error 61 - common solutions did not work"
date: 2014-03-04
forum: General Help
---

### Post by sabbyATL on 2014-03-04
I know there have been a lot of posts about this but I can't seem to solve it.

I've been using the Citrix Receiver on my 64-bit machine for more than two years.  On Friday, it stopped working and gave me the SSL error 61.  I was, at the time, using Pear OS.  I'd already decided to switch back to Ubuntu since Pear isn't being developed and because, well, I keep coming back to Ubuntu.  I like to try different distros for fun but I generally come back to Ubuntu.  And the Citric Receiver has always worked on Ubuntu.

Soooo, when it stopped working on Friday I didn't think much of it.  I was already thinking about installing Ubuntu.  Not as a fix but just that I didn't really think about it and was thinking about doing the install, etc.  

After I installed Ubuntu 13.10 I installed the 64-bit Citrix Receiver, following the instructions [here]("https://help.ubuntu.com/community/CitrixICAClientHowTo") down to the letter.

I am able to log on but I am not able to access my remote desktop. When I log on I am provided with a link to the remote desktop. When I click on the link I get a pop-up that says:

> Contact your help desk with the following information: You have not chosen to trust "VeriSign Class 3 Secure Server CA - G3", the issuer of the server's security certificate (SSL error 61).

First I called my help desk. They told me they only support Windows. And then they told me they don't have anything to do with the certificates and that's an issue between my non-Windows browser and Citrix. 

Second, I've tried some of the solutions I've searched for on the internet, including on this forum:

1. I went to a Windows computer and exported the certificate, changed the extension from .cer to .crt, and imported it into FireFox. Didn't work.
2. I saved that same certificate to /opt/Citrix/ICAClient/keystore/cacerts. Didn't work.
3. I tried exporting from FireFox into /opt/Citrix/ICAClient/keystore/cacerts. Didn't work.
4. I tried different browers - Chromium, Chrome, Midori, Opera. Didn't work.
5. I went to VeriSign and [checked my certificate chain]("https://ssltools.websecurity.symantec.com/checker/views/certCheck.jsp") and it said:

> Root installed on the server.
For best practices, remove the self-signed root from the server.


Update your certificate chain.
Your certificate chain is valid, but some older browsers may not recognize it. To support older browsers, download and install the missing intermediate certificate. | [Download certificate]("https://ssltools.websecurity.symantec.com/chainTester/webservice/validatecerts/certificate?certKey=issuer.crosssigning.cert.0&fileName=VeriSign%20Class%203%20Public%20Primary%20Certification%20Authority%20-%20G5&fileExtension=txt")



What does that mean and can I fix it?  

I did download the certificate and imported it to FireFox, and saved it to /opt/Citrix/ICAClient/keystore/cacerts but that didn't work.

I don't know what to do now.  I telework two days a week and need to access my remote desktop to do so.  I've made do by using my son's Windows computer but, as you can image, it's far from ideal.

---

### Post by sabbyATL on 2014-03-05
Nothing?  No one can help me?

---

### Post by ouelletjon on 2014-03-14
Rename the extention on the file to .crt and include it in this directory /opt/Citrix/ICAClient/keystore/cacert

---

### Post by sabbyATL on 2014-03-17
> **ouelletjon said:**
> Rename the extention on the file to .crt and include it in this directory /opt/Citrix/ICAClient/keystore/cacert



Hi, thanks, I tried that.  It didn't work.

For now I am using Internet Explorer via VirtualBox but it's not ideal.

---

### Post by Teobaldo_Percy_Ch on 2014-05-01
Download the "[COLOR=#000000]*VeriSign Class 3 Secure Server CA - G3*[/COLOR]" root certificate [here]("http://crl.verisign.com/SVRSecureG3.cer") and copy it to [COLOR=#000000]*/opt/Citrix/ICAClient/keystore/cacert*[/COLOR]

---

### Post by sabbyATL on 2014-05-02
> **Teobaldo_Percy_Ch said:**
> Download the "[COLOR=#000000]*VeriSign Class 3 Secure Server CA - G3*[/COLOR]" root certificate [here]("http://crl.verisign.com/SVRSecureG3.cer") and copy it to [COLOR=#000000]*/opt/Citrix/ICAClient/keystore/cacert*[/COLOR]

Thanks, but that doesn't work.  I've tried that before.  The official work is that only IE is supported.  But I know that Chrome in Windows works, as well.  Or it does in my VirtualBox version of Windows 7.

---

### Post by evan15 on 2014-07-15
i'm still having this same issue. i've copied all the certs to every folder mentioned in this thread.

could someone please give me a hand?

---

### Post by vobadm on 2014-10-09
sudo ln -s /usr/share/ca-certificates/mozilla/* /opt/Citrix/ICAClient/keystore/cacerts/
sudo c_rehash /opt/Citrix/ICAClient/keystore/cacerts/

should help with the new certificate. At least it worked for me.

Source: [https://help.ubuntu.com/community/CitrixICAClientHowTo](https://help.ubuntu.com/community/CitrixICAClientHowTo)

---

### Post by Doush on 2014-11-28
Great... I dont know what these commands did exactly.. BUT IT WORKS for me..

cheers

---

### Post by dark_harmonics on 2015-05-05
For me, the thawte root CA i needed was not in the certificate chain. I followed the instructions at [https://help.ubuntu.com/community/CitrixICAClientHowTo](https://help.ubuntu.com/community/CitrixICAClientHowTo) to install and configure my ICA client. I then opened the web interface (through a netscaler) of my company's citrix site. I clicked the lock icon (in firefox) and viewed the certificate. I hit the export button and exported each level of the certificate to DER format and named them with a .cer extension. I then placed all the .cer files in /usr/share/ca-certificates/mozilla and performed the commands others have mentioned in this thread to link and rehash the certs:
[COLOR=#000000]sudo ln -s /usr/share/ca-certificates/mozilla/* /opt/Citrix/ICAClient/keystore/cacerts/[/COLOR]
[COLOR=#000000]sudo c_rehash /opt/Citrix/ICAClient/keystore/cacerts/
[/COLOR]
Now that i have the cert chain imported it works like a charm!

---

### Post by michiel-o on 2015-05-05
I got the this problem as well in firefox while connecting to a citrix server:

```
This personal certificate can't be installed because you do not own the corresponding private key which was created when the certificate was requested.
```

I managed it to get it to work by exporting the certificate from the browser by clicking on the lock in the browser address bar when connecting to the secure site.
Then "more information" -> "security" -> "view certificate" -> "details".
In the certificate hierarchy I had to take the SECOND certificate to export. Export it as x.509(PEM) format somewhere.
Go to that place and add .crt to the filename.
Put that certificate into /opt/Citrix/ICAClient/keystore/cacerts and voila it worked.

---

### Post by jules7 on 2016-01-18
So much thank you guy , i was on this problem since so long. IT WORKS for me too

---

