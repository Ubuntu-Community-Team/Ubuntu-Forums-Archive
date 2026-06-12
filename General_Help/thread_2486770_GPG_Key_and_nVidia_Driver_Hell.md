---
title: "GPG Key and nVidia Driver Hell"
date: 2023-05-10
forum: General Help
---

### Post by yoshmaista on 2023-05-10
Having problems with my nvidia gpg keys after manually installing some repositories/librarires (cuDNN, TensorRT, CUDA) all of my keys after updating them stopped authenticating via the apt servers.  How do I find the new keys and install them to the keyring?
When I try to install the newest nVidia driver:

```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 nvidia-driver-530 : Depends: libnvidia-gl-530 (= 530.30.02-0ubuntu1) but 530.41.03-0ubuntu0.22.04.2 is to be installed
                     Depends: libnvidia-compute-530 (= 530.30.02-0ubuntu1) but 530.41.03-0ubuntu0.22.04.2 is to be installed
                     Depends: libnvidia-decode-530 (= 530.30.02-0ubuntu1) but it is not going to be installed
                     Depends: libnvidia-encode-530 (= 530.30.02-0ubuntu1) but it is not going to be installed
                     Depends: xserver-xorg-video-nvidia-530 (= 530.30.02-0ubuntu1) but 530.41.03-0ubuntu0.22.04.2 is to be installed
                     Depends: libnvidia-cfg1-530 (= 530.30.02-0ubuntu1) but 530.41.03-0ubuntu0.22.04.2 is to be installed
                     Recommends: nvidia-settings but it is not going to be installed
                     Recommends: nvidia-prime (>= 0.8) but it is not going to be installed
                     Recommends: libnvidia-compute-530:i386 (= 530.30.02-0ubuntu1)
                     Recommends: libnvidia-decode-530:i386 (= 530.30.02-0ubuntu1)
                     Recommends: libnvidia-encode-530:i386 (= 530.30.02-0ubuntu1)
                     Recommends: libnvidia-fbc1-530:i386 (= 530.30.02-0ubuntu1)
                     Recommends: libnvidia-gl-530:i386 (= 530.30.02-0ubuntu1)
E: Unable to correct problems, you have held broken packages.



```

apt-get update and upgrade

```
yosh@yoshdesk:/mnt/2tb/RedditScraper/PyScripts$ sudo apt-get update && sudo apt-get upgradeGet:1 file:/var/cuda-repo-ubuntu2204-12-1-local  InRelease [1,572 B]
Get:2 file:/var/cudnn-local-repo-ubuntu2204-8.9.1.23  InRelease [1,572 B]
Get:1 file:/var/cuda-repo-ubuntu2204-12-1-local  InRelease [1,572 B]
Get:3 file:/var/nccl-local-repo-ubuntu2204-2.18.1-cuda12.1  InRelease [1,572 B]
Get:2 file:/var/cudnn-local-repo-ubuntu2204-8.9.1.23  InRelease [1,572 B]
Get:4 file:/var/nv-tensorrt-local-repo-ubuntu2204-8.6.1-cuda-12.0  InRelease [1,572 B]
Get:3 file:/var/nccl-local-repo-ubuntu2204-2.18.1-cuda12.1  InRelease [1,572 B]
Get:4 file:/var/nv-tensorrt-local-repo-ubuntu2204-8.6.1-cuda-12.0  InRelease [1,572 B]
Err:2 file:/var/cudnn-local-repo-ubuntu2204-8.9.1.23  InRelease                                                         
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 26253C7BE7A7D88D
Err:3 file:/var/nccl-local-repo-ubuntu2204-2.18.1-cuda12.1  InRelease                                                                                                                                                                                                                                                                                                                   
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4DD62C54C6F7544F
Hit:5 http://developer.download.nvidia.com/compute/cuda/repos/ubuntu2004/x86_64  InRelease                                                                                                                                                                                                                                                                                              
Hit:6 http://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64  InRelease                                                                                                                                                                                                                                                                                              
Err:4 file:/var/nv-tensorrt-local-repo-ubuntu2204-8.6.1-cuda-12.0  InRelease                                                                                                                                                                                                                                                                                             
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 14E4F55442B2FC56
Hit:7 http://us.archive.ubuntu.com/ubuntu jammy InRelease                                                                                                                                                                                                                                                                                       
Hit:8 https://storage.googleapis.com/bazel-apt stable InRelease                                                                                                                                                                                                                                                                                 
Hit:9 https://developer.download.nvidia.com/hpc-sdk/ubuntu/amd64  InRelease                                                                                                                                                                                                                                               
Hit:10 https://deb.opera.com/opera-stable stable InRelease                                                                                                                                                                                                                                          
Hit:11 http://us.archive.ubuntu.com/ubuntu jammy-updates InRelease                                                                                                                                          
Hit:12 http://us.archive.ubuntu.com/ubuntu jammy-backports InRelease                                                                                                                  
Get:13 https://esm.ubuntu.com/apps/ubuntu jammy-apps-security InRelease [7,553 B]                                                                                                     
Hit:14 http://security.ubuntu.com/ubuntu jammy-security InRelease                                                                                                             
Get:15 https://esm.ubuntu.com/apps/ubuntu jammy-apps-updates InRelease [7,459 B]                                                          
Hit:16 https://packages.microsoft.com/repos/vscode stable InRelease                                                      
Get:17 https://esm.ubuntu.com/infra/ubuntu jammy-infra-security InRelease [7,453 B]  
Get:18 https://esm.ubuntu.com/infra/ubuntu jammy-infra-updates InRelease [7,452 B]   
Hit:19 https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu jammy InRelease
Reading package lists... Done
W: GPG error: file:/var/cudnn-local-repo-ubuntu2204-8.9.1.23  InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 26253C7BE7A7D88D
E: The repository 'file:/var/cudnn-local-repo-ubuntu2204-8.9.1.23  InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: file:/var/nccl-local-repo-ubuntu2204-2.18.1-cuda12.1  InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4DD62C54C6F7544F
E: The repository 'file:/var/nccl-local-repo-ubuntu2204-2.18.1-cuda12.1  InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: file:/var/nv-tensorrt-local-repo-ubuntu2204-8.6.1-cuda-12.0  InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 14E4F55442B2FC56
E: The repository 'file:/var/nv-tensorrt-local-repo-ubuntu2204-8.6.1-cuda-12.0  InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: Target Packages (Packages) is configured multiple times in /etc/apt/sources.list.d/archive_uri-http_developer_download_nvidia_com_compute_cuda_repos_ubuntu2004_x86_64_-jammy.list:1 and /etc/apt/sources.list.d/cuda-ubuntu2004-x86_64.list:1
W: Target Translations (en_US) is configured multiple times in /etc/apt/sources.list.d/archive_uri-http_developer_download_nvidia_com_compute_cuda_repos_ubuntu2004_x86_64_-jammy.list:1 and /etc/apt/sources.list.d/cuda-ubuntu2004-x86_64.list:1
W: Target Translations (en) is configured multiple times in /etc/apt/sources.list.d/archive_uri-http_developer_download_nvidia_com_compute_cuda_repos_ubuntu2004_x86_64_-jammy.list:1 and /etc/apt/sources.list.d/cuda-ubuntu2004-x86_64.list:1
W: http://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/InRelease: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
W: https://deb.opera.com/opera-stable/dists/stable/InRelease: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
W: https://esm.ubuntu.com/apps/ubuntu/dists/jammy-apps-security/InRelease: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
W: https://esm.ubuntu.com/apps/ubuntu/dists/jammy-apps-updates/InRelease: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
W: https://packages.microsoft.com/repos/vscode/dists/stable/InRelease: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
W: https://esm.ubuntu.com/infra/ubuntu/dists/jammy-infra-security/InRelease: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
W: https://esm.ubuntu.com/infra/ubuntu/dists/jammy-infra-updates/InRelease: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
W: https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu/dists/jammy/InRelease: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
W: Target Packages (Packages) is configured multiple times in /etc/apt/sources.list.d/archive_uri-http_developer_download_nvidia_com_compute_cuda_repos_ubuntu2004_x86_64_-jammy.list:1 and /etc/apt/sources.list.d/cuda-ubuntu2004-x86_64.list:1
W: Target Translations (en_US) is configured multiple times in /etc/apt/sources.list.d/archive_uri-http_developer_download_nvidia_com_compute_cuda_repos_ubuntu2004_x86_64_-jammy.list:1 and /etc/apt/sources.list.d/cuda-ubuntu2004-x86_64.list:1
W: Target Translations (en) is configured multiple times in /etc/apt/sources.list.d/archive_uri-http_developer_download_nvidia_com_compute_cuda_repos_ubuntu2004_x86_64_-jammy.list:1 and /etc/apt/sources.list.d/cuda-ubuntu2004-x86_64.list:1

```

Halp

---

### Post by MAFoElffen on 2023-05-10
For these errors:
```

Err:2 file:/var/cudnn-local-repo-ubuntu2204-8.9.1.23  InRelease                                                         
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 26253C7BE7A7D88D
Err:3 file:/var/nccl-local-repo-ubuntu2204-2.18.1-cuda12.1 InRelease                                                                                                                                                                                                                                                                                                                   
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4DD62C54C6F7544F
Err:4 file:/var/nv-tensorrt-local-repo-ubuntu2204-8.6.1-cuda-12.0  InRelease                                                                                                                                                                                                                                                                                             
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 14E4F55442B2FC56
W: GPG error: file:/var/cudnn-local-repo-ubuntu2204-8.9.1.23  InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 26253C7BE7A7D88D
W: GPG error: file:/var/nccl-local-repo-ubuntu2204-2.18.1-cuda12.1  InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4DD62C54C6F7544F
W: GPG error: file:/var/nv-tensorrt-local-repo-ubuntu2204-8.6.1-cuda-12.0  InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 14E4F55442B2FC56

```
At least for nVidia Cuda, nVidia updated their signing keys for their Repo. They published the instructions to update their keys: [https://developer.nvidia.com/blog/updating-the-cuda-linux-gpg-repository-key/](https://developer.nvidia.com/blog/updating-the-cuda-linux-gpg-repository-key/)

---

### Post by yoshmaista on 2023-05-10
Yeah was the first thing I tried a couple days ago.  
```

--2023-05-10 05:48:16--  https://developer.download.nvidia.com/compute/cuda/repos///cuda-keyring_1.0-1_all.deb
Resolving developer.download.nvidia.com (developer.download.nvidia.com)... 152.195.19.142
Connecting to developer.download.nvidia.com (developer.download.nvidia.com)|152.195.19.142|:443... connected.
HTTP request sent, awaiting response... 404 Not Found
2023-05-10 05:48:17 ERROR 404: Not Found.

```

---

### Post by yoshmaista on 2023-05-10
even  after replacing  the GPG keys
```

Hit:19 https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu jammy InRelease  
Reading package lists... Done
W: GPG error: file:/var/cudnn-local-repo-ubuntu2204-8.9.1.23  InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 26253C7BE7A7D88D
E: The repository 'file:/var/cudnn-local-repo-ubuntu2204-8.9.1.23  InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: file:/var/nccl-local-repo-ubuntu2204-2.18.1-cuda12.1  InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4DD62C54C6F7544F
E: The repository 'file:/var/nccl-local-repo-ubuntu2204-2.18.1-cuda12.1  InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: file:/var/nv-tensorrt-local-repo-ubuntu2204-8.6.1-cuda-12.0  InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 14E4F55442B2FC56
E: The repository 'file:/var/nv-tensorrt-local-repo-ubuntu2204-8.6.1-cuda-12.0  InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: Target Packages (Packages) is configured multiple times in /etc/apt/sources.list.d/archive_uri-http_developer_download_nvidia_com_compute_cuda_repos_ubuntu2004_x86_64_-jammy.list:1 and /etc/apt/sources.list.d/cuda-ubuntu2004-x86_64.list:1
W: Target Translations (en_US) is configured multiple times in /etc/apt/sources.list.d/archive_uri-http_developer_download_nvidia_com_compute_cuda_repos_ubuntu2004_x86_64_-jammy.list:1 and /etc/apt/sources.list.d/cuda-ubuntu2004-x86_64.list:1
W: Target Translations (en) is configured multiple times in /etc/apt/sources.list.d/archive_uri-http_developer_download_nvidia_com_compute_cuda_repos_ubuntu2004_x86_64_-jammy.list:1 and /etc/apt/sources.list.d/cuda-ubuntu2004-x86_64.list:1
W: Target Packages (Packages) is configured multiple times in /etc/apt/sources.list.d/archive_uri-http_developer_download_nvidia_com_compute_cuda_repos_ubuntu2204_x86_64_-jammy.list:1 and /etc/apt/sources.list.d/cuda-ubuntu2204-x86_64.list:1
W: Target Translations (en_US) is configured multiple times in /etc/apt/sources.list.d/archive_uri-http_developer_download_nvidia_com_compute_cuda_repos_ubuntu2204_x86_64_-jammy.list:1 and /etc/apt/sources.list.d/cuda-ubuntu2204-x86_64.list:1
W: Target Translations (en) is configured multiple times in /etc/apt/sources.list.d/archive_uri-http_developer_download_nvidia_com_compute_cuda_repos_ubuntu2204_x86_64_-jammy.list:1 and /etc/apt/sources.list.d/cuda-ubuntu2204-x86_64.list:1
W: https://esm.ubuntu.com/apps/ubuntu/dists/jammy-apps-security/InRelease: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
W: https://esm.ubuntu.com/apps/ubuntu/dists/jammy-apps-updates/InRelease: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
W: https://packages.microsoft.com/repos/vscode/dists/stable/InRelease: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
W: https://esm.ubuntu.com/infra/ubuntu/dists/jammy-infra-security/InRelease: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
W: https://esm.ubuntu.com/infra/ubuntu/dists/jammy-infra-updates/InRelease: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
W: https://deb.opera.com/opera-stable/dists/stable/InRelease: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
W: https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu/dists/jammy/InRelease: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
W: Target Packages (Packages) is configured multiple times in /etc/apt/sources.list.d/archive_uri-http_developer_download_nvidia_com_compute_cuda_repos_ubuntu2004_x86_64_-jammy.list:1 and /etc/apt/sources.list.d/cuda-ubuntu2004-x86_64.list:1
W: Target Translations (en_US) is configured multiple times in /etc/apt/sources.list.d/archive_uri-http_developer_download_nvidia_com_compute_cuda_repos_ubuntu2004_x86_64_-jammy.list:1 and /etc/apt/sources.list.d/cuda-ubuntu2004-x86_64.list:1
W: Target Translations (en) is configured multiple times in /etc/apt/sources.list.d/archive_uri-http_developer_download_nvidia_com_compute_cuda_repos_ubuntu2004_x86_64_-jammy.list:1 and /etc/apt/sources.list.d/cuda-ubuntu2004-x86_64.list:1
W: Target Packages (Packages) is configured multiple times in /etc/apt/sources.list.d/archive_uri-http_developer_download_nvidia_com_compute_cuda_repos_ubuntu2204_x86_64_-jammy.list:1 and /etc/apt/sources.list.d/cuda-ubuntu2204-x86_64.list:1
W: Target Translations (en_US) is configured multiple times in /etc/apt/sources.list.d/archive_uri-http_developer_download_nvidia_com_compute_cuda_repos_ubuntu2204_x86_64_-jammy.list:1 and /etc/apt/sources.list.d/cuda-ubuntu2204-x86_64.list:1
W: Target Translations (en) is configured multiple times in /etc/apt/sources.list.d/archive_uri-http_developer_download_nvidia_com_compute_cuda_repos_ubuntu2204_x86_64_-jammy.list:1 and /etc/apt/sources.list.d/cuda-ubuntu2204-x86_64.list:1
root@yoshdesk:/mnt/2tb/RedditScraper/PyScripts# sudo apt install nvidia-driver-530
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 nvidia-driver-530 : Depends: libnvidia-gl-530 (= 530.30.02-0ubuntu1) but 530.41.03-0ubuntu0.22.04.2 is to be installed
                     Depends: libnvidia-compute-530 (= 530.30.02-0ubuntu1) but 530.41.03-0ubuntu0.22.04.2 is to be installed
                     Depends: libnvidia-decode-530 (= 530.30.02-0ubuntu1) but it is not going to be installed
                     Depends: libnvidia-encode-530 (= 530.30.02-0ubuntu1) but it is not going to be installed
                     Depends: xserver-xorg-video-nvidia-530 (= 530.30.02-0ubuntu1) but 530.41.03-0ubuntu0.22.04.2 is to be installed
                     Depends: libnvidia-cfg1-530 (= 530.30.02-0ubuntu1) but 530.41.03-0ubuntu0.22.04.2 is to be installed
                     Recommends: nvidia-settings but it is not going to be installed
                     Recommends: nvidia-prime (>= 0.8) but it is not going to be installed
                     Recommends: libnvidia-compute-530:i386 (= 530.30.02-0ubuntu1)
                     Recommends: libnvidia-decode-530:i386 (= 530.30.02-0ubuntu1)
                     Recommends: libnvidia-encode-530:i386 (= 530.30.02-0ubuntu1)
                     Recommends: libnvidia-fbc1-530:i386 (= 530.30.02-0ubuntu1)
                     Recommends: libnvidia-gl-530:i386 (= 530.30.02-0ubuntu1)
E: Unable to correct problems, you have held broken packages.

```

Please make it something stupid I can hate myself for forgetting.

---

### Post by MAFoElffen on 2023-05-10
> **yoshmaista said:**
> Yeah was the first thing I tried a couple days ago.  
```

--2023-05-10 05:48:16--  https://developer.download.nvidia.com/compute/cuda/repos///cuda-keyring_1.0-1_all.deb
Resolving developer.download.nvidia.com (developer.download.nvidia.com)... 152.195.19.142
Connecting to developer.download.nvidia.com (developer.download.nvidia.com)|152.195.19.142|:443... connected.
HTTP request sent, awaiting response... [COLOR=#ff0000]404 Not Found
2023-05-10 05:48:17 ERROR 404: Not Found.[/COLOR]

```
That failed. The file is not there. It's going to continue to get that error until it is successful.

I went to: [https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/](https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/)
And looked for the package. I confirmed it is not there.

**UPDATE:** I went to the nVidia Tecnical Blog on where they had been talking about this... Seems that package is gone and the the instructions did change...
[https://forums.developer.nvidia.com/t/updating-the-cuda-linux-gpg-repository-key/212897/38?page=3](https://forums.developer.nvidia.com/t/updating-the-cuda-linux-gpg-repository-key/212897/38?page=3)

---

### Post by yoshmaista on 2023-05-10
Fixed the problem only to have another problem pop up:

```
yosh@yoshdesk:/mnt/2tb/RedditScraper/PyScripts$ sudo apt install nvidia-driver-530Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 nvidia-driver-530 : Depends: libnvidia-gl-530 (= 530.30.02-0ubuntu1) but 530.41.03-0ubuntu0.22.04.2 is to be installed
                     Depends: libnvidia-compute-530 (= 530.30.02-0ubuntu1) but 530.41.03-0ubuntu0.22.04.2 is to be installed
                     Depends: libnvidia-decode-530 (= 530.30.02-0ubuntu1) but it is not going to be installed
                     Depends: libnvidia-encode-530 (= 530.30.02-0ubuntu1) but it is not going to be installed
                     Depends: xserver-xorg-video-nvidia-530 (= 530.30.02-0ubuntu1) but 530.41.03-0ubuntu0.22.04.2 is to be installed
                     Depends: libnvidia-cfg1-530 (= 530.30.02-0ubuntu1) but 530.41.03-0ubuntu0.22.04.2 is to be installed
                     Recommends: nvidia-settings but it is not going to be installed
                     Recommends: nvidia-prime (>= 0.8) but it is not going to be installed
                     Recommends: libnvidia-compute-530:i386 (= 530.30.02-0ubuntu1)
                     Recommends: libnvidia-decode-530:i386 (= 530.30.02-0ubuntu1)
                     Recommends: libnvidia-encode-530:i386 (= 530.30.02-0ubuntu1)
                     Recommends: libnvidia-fbc1-530:i386 (= 530.30.02-0ubuntu1)
                     Recommends: libnvidia-gl-530:i386 (= 530.30.02-0ubuntu1)
E: Unable to correct problems, you have held broken packages.

```

---

### Post by yoshmaista on 2023-05-10
There's some instructions kind of hidden  in the first link--it worked.  I glossed over them initially.  Thanks!

---

### Post by MAFoElffen on 2023-05-10
LOL. So this is solved now?

If so please post a summary of what worked for you and mark the thread as "Solved" so that others may find what worked for you. (Share the knowledge.)

---

### Post by yoshmaista on 2023-05-11
> **MAFoElffen said:**
> LOL. So this is solved now?

If so please post a summary of what worked for you and mark the thread as "Solved" so that others may find what worked for you. (Share the knowledge.)

If this was solved I'd have done that.  I got a couple gpg keys installed, still getting errors and still unable to install nvidia drivers on Ubuntu.  About to reinstall Ubuntu because I can't find a fix.

---

### Post by MAFoElffen on 2023-05-11
My misunderstanding by what you had said...

What errors are (still) you getting now?

---

### Post by MAFoElffen on 2023-05-11
Hmmm... I looked through the nVidia Repo.

What about if you first checked for old nvidia/Cuda keys with
```

sudo apt-key list

```
And deleting the old keys, then do
```

wget -N -t 5 -T 10 http://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/cuda-keyring_1.1-1_all.deb
sudo dpkg -i ./cuda-keyring_1.1-1_all.deb
sudo apt update
sudo apt upgrade

```

---

