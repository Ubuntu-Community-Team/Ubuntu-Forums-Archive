---
title: "winbindd unable to initalize domain list?"
date: 2007-01-03
forum: General Help
---

### Post by dannyboy79 on 2007-01-03
In an attempt to get my 2 ubuntu machines and my winxp machine to all play nice I installed samba and read some where that winbind also helps out? I changed my /etc/nsswitch.conf file so that this line was present:
hosts:          files dns wins

and for the most part everything is working. I can see my ubuntu box from my xbox and from winxp but the problem is that when I can't see my winxp box thru xubuntu when I use xsmbrowser or when I do smbtree? I noticed this is a log file that was emailed to me after I installed logcheck. 

Jan  1 22:20:08 ubuntu winbindd[5220]: [2007/01/01 22:20:08, 0] nsswitch/winbindd.c:main(1071)
Jan  1 22:20:08 ubuntu winbindd[5220]:   unable to initalize domain list

Can anyone help me figure out why winxp won't show me it's shares. What's more weird is that I can do smbclient -L WINXP and get this:
Domain=[WINXP] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------       ----      -------
        E$              Disk      Default share
        My Documents    Disk
        newmovies       Disk
        IPC$            IPC       Remote IPC
        print$          Disk      Printer Drivers
        SharedDocs      Disk
        I$              Disk      Default share
        xbox            Disk
        Pictures        Disk      pictures in my docs
        AdobePDF        Printer   Creates Adobe PDF
        G$              Disk      Default share
        HPOfficeJet     Printer   hp officejet d series
        Printer2        Printer   Lexmark Z700-P700 Series
        ADMIN$          Disk      Remote Admin
        H$              Disk      Default share
        C$              Disk      Default share
        Printer         Printer   Microsoft Office Document Image Writer
Domain=[WINXP] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------

So I know that WINXP has shares on it. Another weird thing is that smbtree returns nothing and when I do findsmb it only shows xubuntu and ubuntu? All the usernames and password are the same on all 3 machines and I have that same user added to smbpasswd. I am using security=user in my cmb.conf. Oh, if this matters I can ping by both hostname as well as ip.  I would really appreciate any help with this.

---

### Post by dannyboy79 on 2007-02-07
hello, please some1 help me with this.

---

