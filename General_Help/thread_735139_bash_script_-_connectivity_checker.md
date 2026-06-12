---
title: "bash script - connectivity checker"
date: 2008-03-25
forum: General Help
---

### Post by phillips321 on 2008-03-25
hi guys,

i would like to create a bash script that checks for connectivity and then executes commands if their is a viable connection.

it will need to check 3 interfaces, eth0 ppp0 and ath0.

does anyone know how do do this?

cheers

---

### Post by lloyd_b on 2008-03-25
> **phillips321 said:**
> hi guys,

i would like to create a bash script that checks for connectivity and then executes commands if their is a viable connection.

it will need to check 3 interfaces, eth0 ppp0 and ath0.

does anyone know how do do this?

cheers

Here's a very simple script to check internet connectivity:
```

#!/bin/bash

if eval "ping -c 1 www.google.com"; then
    echo "We've got internet"
else
    echo "No internet available"
fi
```

What this does is send a single ping packet to "www.google.com", and test the return value from the ping command.

Note that if you're not testing for internet connectivity, but connectivity to a LAN, you can just ping against an IP address on the LAN and accomplish the same thing.  

Lloyd B.

---

