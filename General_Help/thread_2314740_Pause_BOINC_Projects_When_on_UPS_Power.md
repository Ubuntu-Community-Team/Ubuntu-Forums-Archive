---
title: "Pause BOINC Projects When on UPS Power"
date: 2016-02-23
forum: General Help
---

### Post by harrispartyof3 on 2016-02-23
I have an ubuntu server setup, currently been running for 300+ days. Currently I have BOINC (an "Open-source software for volunteer computing" program) that runs every night on a time schedule. The problem I'm foreseeing is the power goes out at night while BOINC is running and the UPS doesn't last long enough for the power to come back up. When the server is idle the ups can sustain the server for 3ish hours if i remember correctly, but under the load BOINC puts on it the ups can only run for 25 minutes before shutting the server down, you can see why I would rather preserve battery power in hopes of power coming back to prevent an unnecessary shutdown.

What I'm wondering is if there is a way to pause BOINC (or maybe set a cpu cap for the BOINC children processes to .1%) whenever the power goes out? 

The server monitors the ups with NUT (Network Ups Tools) to get telemetries back from the ups so ubuntu knows the current state of the ups. There is a “Do work while on battery?” check box in BOINC that will pause the processing when a laptop is unplugged but I don't believe that this will work with the ups on a desktop, maybe this option in BOINC can be utilized somehow to get a somewhat seamless integration of the UPS into BOINC.

Not sure if the only solution is a homemade program or maybe I'm lucky enough that theres an existing solution, any ideas?
Thanks

---

