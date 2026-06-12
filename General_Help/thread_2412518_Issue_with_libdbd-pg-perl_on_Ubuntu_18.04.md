---
title: "Issue with libdbd-pg-perl on Ubuntu 18.04"
date: 2019-02-14
forum: General Help
---

### Post by tslai on 2019-02-14
Hi There,

I tried to install libdbd-pg-perl in my enviroment with following commands (Ubuntu 18.04.1 LTS (GNU/Linux 4.15.0-43-generic x86_64))
i.e. 
```

sudo apt-get update
sudo apt-get install libdbd-pg-perl

```

However, the installation was not successful that packages have unmet dependencies.
```

tslai@dev:~$ sudo apt-get install libdbd-pg-perl
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 libdbd-pg-perl : Depends: perlapi-5.22.1
E: Unable to correct problems, you have held broken packages.

```

I also tried to install perlapi-5.26.1 / perlapi-5.22.1, but neither of these help.
```

tslai@dev:~$ sudo apt-get install perlapi-5.26.1
Reading package lists... Done
Building dependency tree
Reading state information... Done
Note, selecting 'perl-base' instead of 'perlapi-5.26.1'
perl-base is already the newest version (5.26.1-6ubuntu0.3).
0 upgraded, 0 newly installed, 0 to remove and 151 not upgraded.

tslai@dev:~$ sudo apt-get install perlapi-5.22.1
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package perlapi-5.22.1 is a virtual package provided by:
  perl-base 5.22.1-9ubuntu0.6 [Not candidate version]


E: Package 'perlapi-5.22.1' has no installation candidate

```


Can anyone please advise me how to install the libdbd-pg-perl on Ubuntu 18.04.

---

### Post by him610 on 2019-02-14
You may have better chance of success if you use *synaptic* to download and install libdbd-pg-perl 
Using synaptic you will see there a couple of other packages that will be installed, libdi-perl and libpq5
There is no entry for perlapi* in synaptic 0.84.3
Did you install perl from the ubuntu repositories?

---

### Post by tslai on 2019-02-18
> **him610 said:**
> You may have better chance of success if you use *synaptic* to download and install libdbd-pg-perl 
Using synaptic you will see there a couple of other packages that will be installed, libdi-perl and libpq5
There is no entry for perlapi* in synaptic 0.84.3
Did you install perl from the ubuntu repositories?

Where can I check if perl is installed from ubuntu repositories?

---

