---
title: "ClamAV reporting itself?"
date: 2008-06-11
forum: General Help
---

### Post by ShinHadoken on 2008-06-11
I did a clamscan last night, and it found these five files:

```

//usr/share/clamav-testfiles/clam.cab: ClamAV-Test-File FOUND
//usr/share/clamav-testfiles/clam.exe: ClamAV-Test-File FOUND
//usr/share/clamav-testfiles/clam.zip: ClamAV-Test-File FOUND
//usr/share/clamav-testfiles/clam.exe.bz2: ClamAV-Test-File FOUND
//var/lib/clamav-getfiles/eicar.com: Eicar-Test-Signature FOUND

```

These are all ClamAV files! What do I do?

Thanks in advance,

SH

---

### Post by CameO73 on 2008-06-11
Nothing. Those test files are a self-check. If ClamAV wouldn't have found them, something would be wrong (for example a virus that had compromised ClamAV).

---

### Post by ShinHadoken on 2008-06-11
Oh, ok lol. Thx

---

