---
title: "CA Certificates Not Recognized"
date: 2021-08-09
forum: General Help
---

### Post by Holmes89 on 2021-08-09
I've been trying to get CA Certs installed because I'm getting errors when trying to use `rosdep init` which makes calls to "raw.githubusercontent.com". If I do the same call with `wget` I'll get the same error:

```

ERROR: cannot verify raw.githubusercontent.com's certificate, issued by ‘CN=DigiCert SHA2 High Assurance Server CA,OU=www.digicert.com,O=DigiCert Inc,C=US’:
  Unable to locally verify the issuer's authority.
```

I have installed ca-certificates. I also tried this on a fresh install and everything worked fine. However, I cannot reinstall on the machine I am on at the moment, is there a way to resolve this some other way?

---

### Post by Holmes89 on 2021-08-09
Some things I've tried.

```

sudo dpkg -s ca-certificates | grep Version 
Version: 20210119~20.04.1

sudo apt-get install --reinstall ca-certificates

ls /etc/ssl/certs/ | grep DigiCert
DigiCert_Assured_ID_Root_CA.pem
DigiCert_Assured_ID_Root_G2.pem
DigiCert_Assured_ID_Root_G3.pem
DigiCert_Global_Root_CA.pem
DigiCert_Global_Root_G2.pem
DigiCert_Global_Root_G3.pem
DigiCert_High_Assurance_EV_Root_CA.pem
DigiCert_Trusted_Root_G4.pem

```

---

### Post by Holmes89 on 2021-08-10
When running wget with a --ca-directory flag it seems to work. So I guess my problem is why aren't applications looking at the /etc/ssl/certs directory? Is there a setting somewhere that may have been broken?

---

### Post by Holmes89 on 2021-08-11
I ended up needing to add this to my ~/.bashrc:

```
export SSL_CERT_DIR=/etc/ssl/certs
```

---

