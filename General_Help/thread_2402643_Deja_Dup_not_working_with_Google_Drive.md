---
title: "Deja Dup not working with Google Drive"
date: 2018-10-02
forum: General Help
---

### Post by kyletozer on 2018-10-02
I can't seem to get Deja Dup to work with Google Drive.

I followed this guide: [https://www.omgubuntu.co.uk/2018/07/backup-files-to-google-drive-on-ubuntu](https://www.omgubuntu.co.uk/2018/07/backup-files-to-google-drive-on-ubuntu) and typically the backup does not complete and I will receive an error message after some time.

---

### Post by PaulW2U on 2018-10-03
> **kyletozer said:**
> typically the backup does not complete and I will receive an error message after some time.
But what do the error messages say?

As this is something that I've been meaning to try for some time I decided to backup the entire contents of my home partition and all was going well until about 80% complete when the backup failed with the following error:
```
Giving up after 5 attempts. Error: gdata-service-error-quark: Authentication required: {
 "error": {
  "errors": [
   {
    "domain": "global",
    "reason": "authError",
    "message": "Invalid Credentials",
    "locationType": "header",
    "location": "Authorization"
   }
  ],
  "code": 401,
  "message": "Invalid Credentials"
 }
}
 (4)
```
Is this what you saw? 

This bug report: [Authentication error with google drive [$10]]("https://bugs.launchpad.net/bugs/1747646") seems relevant.

---

### Post by hoos-st on 2018-12-11
11 December and the problem still persists.

Giving up after 5 attempts. Error: gdata-service-error-quark: Authentication required: {
 "error": {
  "errors": [
   {
    "domain": "global",
    "reason": "authError",
    "message": "Invalid Credentials",
    "locationType": "header",
    "location": "Authorization"
   }
  ],
  "code": 401,
  "message": "Invalid Credentials"
 }
}
 (4)

---

### Post by PaulW2U on 2018-12-11
> **hoos-st said:**
> 11 December and the problem still persists.
Indeed it does and with no comments on the bug report to suggest otherwise the issue will of course remain.

I previously confirmed this issue as an Ubuntu user but I've just attempted a backup using Fedora 29 and have been met with
```
Giving up after 5 attempts. Error: Authentication required: {
 "error": {
  "errors": [
   {
    "domain": "global",
    "reason": "authError",
    "message": "Invalid Credentials",
    "locationType": "header",
    "location": "Authorization"
   }
  ],
  "code": 401,
  "message": "Invalid Credentials"
 }
}

```
so **not** an Ubuntu problem and one which only the Deja-Dup maintainer(s) can fix.

---

### Post by charleskr on 2019-01-03
Sometimes it works, sometimes it doesnt. . .

BUT

I have managed to get it to pass by selecting specific folders to backup instead of everything. It seems there is some files/folders it doesnt want to upload.

EDIT: It seems I can upload/backup everything except my Eclipse IDE/WorkSpace...everything else seems to backup just fine...

---

