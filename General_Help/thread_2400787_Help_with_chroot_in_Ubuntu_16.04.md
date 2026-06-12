---
title: "Help with chroot in Ubuntu 16.04"
date: 2018-09-10
forum: General Help
---

### Post by carbochem on 2018-09-10
Okay so I have a server running Ubuntu 16.04 and I need to have a user who can ssh into the server but is chrooted to his home folder. Apart from that, this user must be able to use apt-get, add repositories, etc being inside the chroot and not having sudo access.


So this is what I have done so far:


```
groupadd sshg


useradd -m test -G sshg
echo test:test | chpasswd


# Since this stuff uses keys, I choose to enable password authentication in sshd
cp /etc/ssh/sshd_config /etc/ssh/sshd_config.before_chroot
cat /etc/ssh/sshd_config | sed -e "s/PasswordAuthentication no/PasswordAuthentication yes/" > /etc/ssh/temp_sshd_config
mv -f /etc/ssh/temp_sshd_config /etc/ssh/sshd_config


echo "Match Group sshg" >> /etc/ssh/sshd_config
echo "    ChrootDirectory /home/%u" >> /etc/ssh/sshd_config
echo "    AllowTcpForwarding no" >> /etc/ssh/sshd_config


# Helps in setting the PS1 value for ssh to test user
cp /home/ubuntu/.bashrc /home/test/


# Fixing permissions for chroot
chown root /home/test
chmod go-w /home/test
mkdir /home/test/idkwhatfolder
chown test:sshg /home/test/idkwhatfolder
chmod ug+rwX /home/test/idkwhatfolder


# To get base files inside chroot directory
apt-get install debootstrap
debootstrap --arch=amd64 xenial /home/test http://archive.ubuntu.com/ubuntu/


# restart ssh service
systemctl restart sshd



```SSH'ing as user "test" and typing in something like this "add-apt-repository ppa:webupd8team/java" throws an error "-sh: 4: add-apt-repository: not found"


What should I do, Thanks!

---

### Post by TheFu on 2018-09-10
If you allow apt-get, then you've given them the power of root and root can break out of any chroot environment.
Perhaps you should look for a different technology like containers or virtual machines?

---

