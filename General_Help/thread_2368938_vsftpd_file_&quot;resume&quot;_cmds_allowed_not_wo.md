---
title: "vsftpd file &quot;resume&quot; cmds_allowed not working"
date: 2017-08-16
forum: General Help
---

### Post by Scott_Lindner on 2017-08-16
I'm having troubles getting file "resume" working. I understand the way to enable it is to allow the APPE command. At least that's how older discussions read. When I add a "cmds_allowed" my FTP clients get wonky and partially list directories. It doesn't really work. The client says it's trying a LIST command which I have in cmds_allowed. Here is my complete cmds_allowed list. Am I missing something?
```
cmds_allowed=ABOR,CWD,DELE,LIST,MDTM,MKD,NLST,PASS,PASV,PORT,PWD,QUIT,RETR,RMD,RNFR,RNTO,SITE,SIZE,STOR,TYPE,USER,ACCT,APPE,CDUP,HELP,MODE,NOOP,REIN,STAT,STOU,STRU,SYST
```

---

