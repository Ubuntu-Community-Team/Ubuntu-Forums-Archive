---
title: "Command to find Power Supply Unit - Desktop PC"
date: 2021-11-09
forum: General Help
---

### Post by satimis on 2021-11-09
Hi all,

Please advise how to find the details of Power Supply Unit, such as maker, model etc. ?

$ sudo dmidecode -t 39```

# dmidecode 3.2
Getting SMBIOS data from sysfs.
SMBIOS 2.7 present.

```

$ sudo pwrstat -status```


The UPS information shows as following:
        Current UPS status:
                State........................ Lost Communication

```

Thanks

Regards

---

### Post by Frogs Hair on 2021-11-09
The following command will work if the computer OEM added the information. my computer is a home-build so there is no such information listed. You could open the case and look if you are using a desktop computer.
```
sudo dmidecode --type 39
```

```
Handle 0x0038, DMI type 39, 22 bytes
System Power Supply
    Power Unit Group: 1
    Location: To Be Filled By O.E.M.
    Name: To Be Filled By O.E.M.
    Manufacturer: To Be Filled By O.E.M.
    Serial Number: To Be Filled By O.E.M.
    Asset Tag: To Be Filled By O.E.M.
    Model Part Number: To Be Filled By O.E.M.
    Revision: To Be Filled By O.E.M.

```

---

### Post by satimis on 2021-11-09
> **Frogs Hair said:**
> The following command will work if the computer OEM added the information. my computer is a home-build so there is no such information listed. You could open the case and look if you are using a desktop computer.
```
sudo dmidecode --type 39
```

```
Handle 0x0038, DMI type 39, 22 bytes
System Power Supply
    Power Unit Group: 1
    Location: To Be Filled By O.E.M.
    Name: To Be Filled By O.E.M.
    Manufacturer: To Be Filled By O.E.M.
    Serial Number: To Be Filled By O.E.M.
    Asset Tag: To Be Filled By O.E.M.
    Model Part Number: To Be Filled By O.E.M.
    Revision: To Be Filled By O.E.M.

```
Hi,

Thanks for your advice.

My desktop PC was built by me about 10 years ago.  So the only solution for me is to open the case and look at the power supply for detail.

Regards

---

