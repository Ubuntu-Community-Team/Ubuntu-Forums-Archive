---
title: "How do you compare directories?"
date: 2007-09-07
forum: General Help
---

### Post by wwuster on 2007-09-07
I have 2 Ubuntu machines with the same directory name containing about 30000 files in subdirectories under the parent directory. I'd like to see which files are different between the two machines. Does anyone know a good way to do this? I know that rsync can copy files that are different, but I'd just like to look at what the differences are. Windows has some good programs for this that I've used: "Beyond Compare" and "Filesync". Is there anything like this for linux?

thanks,
William

---

### Post by eggdeng on 2007-09-07
```
diff -r dir1 dir2
``` will do this on local directories. Perhaps if you could mount the remote directory locally? Be interested to hear how you get on with this.

---

### Post by eggdeng on 2007-09-14
Worked out how to do this using SSH. You need to have the SSH server installed on the remote machine ```
apt-get install openssh-server
``` More info at [https://help.ubuntu.com/community/SSHHowto]("https://help.ubuntu.com/community/SSHHowto")
On the local machine, you need to install sshfs
```
sudo apt-get install sshfs
``` more info at [https://help.ubuntu.com/community/SSHFS]("https://help.ubuntu.com/community/SSHFS")
The next step is to add your user to the fuse group to avoid permissions problems. I skipped this step because of problems with the fuse-utils package and just went with sudo.
Now you can mount the remote directory on the client
```
sudo mkdir ~/my_dir
```
```
sudo sshfs $username@remote_IP:/remote_directory ~/my_dir
```
Now you can use diff with the -q switch
```
sudo diff -rq local_dir ~/my_dir
```
and you should get a list of the files which differ.

---

