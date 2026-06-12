---
title: "ypbind not starting"
date: 2007-05-07
forum: General Help
---

### Post by leed25d on 2007-05-07
Here is a listing from /etc/rc2.d on my Ubuntu (Feisty Fawn) wks
    S17mysql-ndb-mgm -> ../init.d/mysql-ndb-mgm
    S18mysql-ndb -> ../init.d/mysql-ndb
    S18nis -> ../init.d/nis
    S18portmap -> ../init.d/portmap
    S19autofs -> ../init.d/autofs

Here is the comment from tne /etc/init.d/nis startup file:
    ### BEGIN INIT INFO
    # Required-Start:	$network $portmap
    # Required-Stop:	$portmap
    # Default-Start:	2 3 4 5
    # Default-Stop:		0 1 6
    # Short-Description:	Start NIS client and server daemons.
    # Description:		Start NIS client and server daemons.  NIS is mostly 
    #			used to let several machines in a network share the 
    #			same account information (eg the password file).
    ### END INIT INFO

Should'nt the 
    S18nis -> ../init.d/nis 
be something like 
    S19nis ->../init.d/nis 

to insure that it runs after the portmapper?  I believe that this is
causing grief on my worksation since ypbind appears not to be
starting.  I can start it by hand and demonstrate that NIS works, of I
can mod the link and ypbind starts ok.  Is anyone else experiencin
this?

---

### Post by leed25d on 2007-05-08
I am following up my own post here in an attempt to find out if I am doing something wrong.  The original post got no response.  Is there some clarifying information that is missing? Was it unintelligible in some way?  Was it posted in the wrong forum?

The original was my first post, so please be gentle.

---

### Post by ccorail on 2007-06-04
same problem here ... on 4 differents machines

---

