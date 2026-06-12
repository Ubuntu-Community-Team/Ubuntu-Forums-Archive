---
title: "No internet under default user"
date: 2006-12-28
forum: General Help
---

### Post by rado_london on 2006-12-28
Hey people very strange problem. I have XChat and Skype running under my default user just fine but if I try to browse the WEB I have no connection. I tried Firefox or Epiphany no luck. However if I ping the net it works. When I run Firefox with sudo the internet connection is fine as I type this from here:)

Well anyone any help?

BTW I was cleaning my system through Synaptic before that happenede but I think i didnt delete anything valuable.

---

### Post by tokj on 2006-12-28
Try this:

Type in terminal:
```
adduser your_username dip
```

The group "dip" is the group of users that can access to internet.

---

### Post by rado_london on 2006-12-28
> **tokj said:**
> Try this:

Type in terminal:
```
adduser your_username dip
```

The group "dip" is the group of users that can access to internet.

here is what I ger:
```
The user `rado' is already a member of `dip'.

```

And I still get this in Firefox:
```
Unable to connect

Firefox can't establish a connection to the server at google.co.uk
        
    *   The site could be temporarily unavailable or too busy. Try again in a few
          moments.

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.


      
```

Help me please !

BTW I removed dansguardian and tinyproxy. Is that relevant to the problem?

---

### Post by rado_london on 2006-12-29
New Year BUMP!!!

---

### Post by rado_london on 2007-01-04
> **rado_london said:**
> New Year BUMP!!!

Come on people help me!!!!!!!This drives me crazy!!!!!

---

