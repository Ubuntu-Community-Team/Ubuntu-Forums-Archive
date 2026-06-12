---
title: "Help with installing MATLAB?"
date: 2015-08-19
forum: General Help
---

### Post by sincerelyydavid on 2015-08-19
So I'm pretty new with Linux. I have my matlab installation files in /tmp/matlab.


I first did


    chmod +x install
    
    ./install


and got this as a result:


    ./install: 1: eval: /tmp/matlab/bin/glnxa64/install_unix: Permission denied


So I did


    cd bin/glnxa64
    chmod +x install_unix
    cd ../../ (to the directory where the install file is)


Running `./install` now gives me:


    Preparing installation files ...
    Installing ...
    Finished


The installation clearly hasn't finished, so I don't know what's going on. Running df shows that my /dev/sda5 mounted on / increased its Use% by 50%.

---

### Post by QDR06VV9 on 2015-08-19
Have a look here [https://help.ubuntu.com/community/MATLAB](https://help.ubuntu.com/community/MATLAB)
Some of your commands did not look right to me.
Also could you use code tags when posting the out puts it makes it easier to read.
Regards

---

