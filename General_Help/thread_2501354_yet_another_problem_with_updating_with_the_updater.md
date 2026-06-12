---
title: "yet another problem with updating with the updater.."
date: 2024-10-03
forum: General Help
---

### Post by ronjjjg8885 on 2024-10-03
hello
i get this
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294327&stc=1[/IMG]
maybe it is because of the mullvad browser..

thanks for assistance..

edit..
i don't have a problem with the connection to the interent

---

### Post by deadflowr on 2024-10-03
When you get that run the terminal command
```
sudo apt update
```
And look at what it says.
Post the output if you're not sure what it means.

---

### Post by ronjjjg8885 on 2024-10-03
```
Hit:1 https://repo.protonvpn.com/debian stable InRelease
Hit:2 http://security.ubuntu.com/ubuntu noble-security InRelease               
Hit:3 http://il.archive.ubuntu.com/ubuntu noble InRelease                      
Hit:4 http://il.archive.ubuntu.com/ubuntu noble-updates InRelease             
Hit:5 http://il.archive.ubuntu.com/ubuntu noble-backports InRelease          
Get:6 https://repository.mullvad.net/deb/stable noble InRelease [2,544 B]    
Get:7 https://repository.mullvad.net/deb/stable noble/main amd64 Packages [902 B]
Err:7 https://repository.mullvad.net/deb/stable noble/main amd64 Packages
  File has unexpected size (901 != 902). Mirror sync in progress? [IP: 45.149.104.1 443]
  Hashes of expected file:
   - Filesize:902 [weak]
   - SHA256:8d62918761d1f40624e5c06e8b33ad39d2b8bd9609cce0be5404c0a9bc26f4c2
   - SHA1:55ef1e20cd9dd946755451aa6b95c35ad20a4a04 [weak]
   - MD5Sum:343fcb0af8ba70f6634482b8dbad268b [weak]
  Release file created at: Thu, 03 Oct 2024 08:46:48 +0000
Reading package lists... Done
E: Failed to fetch https://repository.mullvad.net/deb/stable/dists/noble/main/binary-amd64/Packages.gz  File has unexpected size (901 != 902). Mirror sync in progress? [IP: 45.149.104.1 443]
   Hashes of expected file:
    - Filesize:902 [weak]
    - SHA256:8d62918761d1f40624e5c06e8b33ad39d2b8bd9609cce0be5404c0a9bc26f4c2
    - SHA1:55ef1e20cd9dd946755451aa6b95c35ad20a4a04 [weak]
    - MD5Sum:343fcb0af8ba70f6634482b8dbad268b [weak]
   Release file created at: Thu, 03 Oct 2024 08:46:48 +0000
E: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by deadflowr on 2024-10-03
Yep mullvad.
Could be the issue they cite: *Mirror sync in progress?*

You could simply disable the repository for now (temporarily) which will allow Ubuntu normal updates to run.
Then re-enable later.

You can disable it in Software Updater's Settings > Other Software.
Just uncheck the box for the mullvad entry.
And to re-enable just reverse that and check the box again.

---

### Post by ronjjjg8885 on 2024-10-03
but it is not there..

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294328&stc=1[/IMG]

---

### Post by 1fallen on 2024-10-03
Please run:
```
inxi -r
```
It will show where it is located if it is there.

---

### Post by ronjjjg8885 on 2024-10-03
```
Repos:
  No active apt repos in: /etc/apt/sources.list
  Active apt repos in: /etc/apt/sources.list.d/mullvad.list
    1: deb [signed-by=/usr/share/keyrings/mullvad-keyring.asc arch=amd64] https://repository.mullvad.net/deb/stable noble main
  Active apt repos in: /etc/apt/sources.list.d/protonvpn-stable.list
    1: deb [signed-by=/usr/share/keyrings/protonvpn-stable-archive-keyring.gpg] https://repo.protonvpn.com/debian stable main
  Active apt repos in: /etc/apt/sources.list.d/ubuntu.sources
    1: deb http://il.archive.ubuntu.com/ubuntu/ noble noble-updates noble-backports main restricted universe multiverse
    2: deb http://security.ubuntu.com/ubuntu/ noble-security main restricted universe multiverse

```

---

### Post by 1fallen on 2024-10-03
Yep thar she blows.
```
sudo rm -rf /etc/apt/sources.list.d/mullvad.list
```
Then
```
sudo apt clean
sudo apt update
sudo apt upgrade
```

---

### Post by ronjjjg8885 on 2024-10-03
tnx
now the updater works well
but how to return the mullvad repository so i get the updates when they come?

---

### Post by 1fallen on 2024-10-04
First
```
sudo apt install wget
```
next grab the installer
```
wget "https://mullvad.net/download/app/deb/latest" -O mullvad.deb
```
Now from the Directory the .deb is run
```
sudo dpkg -i mullvad.deb
```
I remember this was a problem on 22.04 so if needed
```
sudo apt install -f
```

Another way is to have curl installed:
```
sudo apt install curl
```
This will add the key, and we did not remove that, and we may need to still but for now:
```
sudo curl -fsSLo /usr/share/keyrings/mullvad-keyring.asc https://repository.mullvad.net/deb/mullvad-keyring.asc
```
Now we add the apt repo:
```
echo "deb [signed-by=/usr/share/keyrings/mullvad-keyring.asc arch=$( dpkg --print-architecture )] https://repository.mullvad.net/deb/stable $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/mullvad.list
```

Now update and let us know how this goes.
```
apt search mullvad
Sorting... Done
Full Text Search... Done
mullvad-browser/unknown 13.5.6-1 amd64
  Mullvad Browser

mullvad-vpn/unknown,now 2024.5 amd64 [installed]
  Mullvad VPN client

```

---

### Post by ronjjjg8885 on 2024-10-04
i've typed
```
wget "https://mullvad.net/download/app/deb/latest" -O mullvad.deb
```

and it is downloading but says it will take 45 minutes or so..


i will update after it is finished

edit..

```
apt search mullvad
Sorting... Done
Full Text Search... Done
mullvad-browser/now 13.5.3-1 amd64 [installed,local]
  Mullvad Browser

mullvad-vpn/now 2024.5 amd64 [installed,local]
  Mullvad VPN client

```


is that ok?
if yes, tnx

---

### Post by 1fallen on 2024-10-04
Enjoy :)

---

