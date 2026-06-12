---
title: "MythTV and Ubuntu"
date: 2005-04-08
forum: General Help
---

### Post by kiselblat on 2005-04-08
I've been spinning my wheels on this for a couple of days now.  MythTV requires MySQL to be properly installed and configured and has multiple components.
Most notable the MythTV backend program, which at the end of my multiple attempts fails to properly configure.
```

.
Unpacking replacement mythtv-backend ...
Setting up mythtv-backend (0.16-1) ...
Starting MythTV server: mythbackendSession management error: Authentication
Rejected, reason : None of the authentication protocols specified are supported
and host-based authentication failed
.

``` 

The good news is it actually configures the MythTV database package!  The bad news, if the backend doesn't work, none of it works.
 Any help would be great.

Thanks!

---

### Post by kiselblat on 2005-04-08
Okay - so I think I got the backend to run by logging into the MythTV user (dur), and I have the IP of the backend (my machine) set to localhost because both the backend and the frontend will be running on the same machine.
The backend DOES indeed register for a time, but then it goes away.  I'm not sure what the deal with that is.
Any thoughts?

---

