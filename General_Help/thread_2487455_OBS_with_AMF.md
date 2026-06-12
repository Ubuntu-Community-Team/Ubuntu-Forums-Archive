---
title: "OBS with AMF"
date: 2023-06-05
forum: General Help
---

### Post by ichbinjasokreativ on 2023-06-05
Hi everybody, I've been trying to get OBS to allow me to record with AMF HEVC encoding while still gaming with the open source mesa drivers.
 To do that, I installed Distrobox on my Ubuntu 23.04 installation and set up an arch container.
 The idea is that I can install the proprietary drivers and OBS with AMF support in that container while still keeping the better-for-gaming mesa drivers on my main OS.
 In theory (and according to other people who did the same), this should word. However, for me it does not.
  
 Steps to follow along:
 (in Ubuntu 23.04, note that my username is simply user)


 sudo apt install distrobox -y
 distrobox-create --image docker.io/library/archlinux:latest --name arch --home ~/arch
 distrobox enter arch


 (in the container, I wrote a script to do things for me)


 cd /home/user/arch/
sudo cp /home/user/arch_amf_obs_script/pacman.conf /etc/                   *#this modified pacman.conf file has disabled signature checking for better compatibility*
sudo cp /home/user/arch_amf_obs_script/mirrorlist /etc/pacman.d/      #this modified mirrorlist limits all arch packages to be no younger than 2023-03-23, which is the date my linux-firmware in the ubuntu installation is, for compatibility
sudo pacman -Syyuu                                                                                  #downgrade of all packages to be no younger than 2023-03-23, see above
sudo pacman -Sy --needed base-devel git
git clone [https://aur.archlinux.org/amdgpu-pro-installer.git](https://aur.archlinux.org/amdgpu-pro-installer.git)              #this git installs the proprietary amdgpu-pro drivers that are needed for AMF to work
cd /home/user/arch/amdgpu-pro-installer/
git checkout 7a537ff70a9ce810c49dd11e42d6cf78aaeb17b9           #limiting the youngest possible state to be this commit, which is older than 2023-03-23, for compatibility
makepkg -si                                                                                                 #making the package and installing it
cd /home/user/arch
git clone [https://aur.archlinux.org/obs-studio-amf.git](https://aur.archlinux.org/obs-studio-amf.git)                        #this git containes OBS with support for AMF
cd /home/user/arch/obs-studio-amf
git checkout d97235dd19e437b104e3762bf36c148250ba2083        #limiting the youngest possible state to be this commit, which is older than 2023-03-23, for compatibility
makepkg -si                                                                                                 #making the package and installing it
  
 After all that, when I launch OBS from within the container, it should allow me to select AMF HW ecoding with HEVC under Settings->Output->Advanced, but it sadly doesn't.

 Any ideas?

Edit: I should probably add some more information:
-System is up to date
-Hardware is a laptop with a Ryzen 7 4700u
-AMF HW HEVC is available in OBS under windows

---

