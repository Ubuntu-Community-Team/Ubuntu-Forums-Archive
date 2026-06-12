---
title: "Cuda not linked correctly"
date: 2021-04-19
forum: General Help
---

### Post by dorpapst on 2021-04-19
I am getting crazy with trying to run programmes using Cuda, Tensorflow etc. I have tried to link it in several ways, but it does not work.
```
nvidia-smi
```
shows the existance of CUDA 11.2

When I try the following code:
```
import tensorflow as tf
tf.test.is_gpu_available()

```
I directly get the error message:
```
Could not load dynamic library 'libcudart.so.11.0'; dlerror: libcudart.so.11.0: cannot open shared object file: No such file or directory
```

Other programmes even show me something like that:
```
2021-04-19 15:01:33.482815: W  tensorflow/stream_executor/platform/default/dso_loader.cc:55] Could not  load dynamic library 'libcudart.so.10.0'; dlerror: libcudart.so.10.0:  cannot open shared object file: No such file or directory
2021-04-19  15:01:33.482841: W  tensorflow/stream_executor/platform/default/dso_loader.cc:55] Could not  load dynamic library 'libcublas.so.10.0'; dlerror: libcublas.so.10.0:  cannot open shared object file: No such file or directory
2021-04-19  15:01:33.482864: W  tensorflow/stream_executor/platform/default/dso_loader.cc:55] Could not  load dynamic library 'libcufft.so.10.0'; dlerror: libcufft.so.10.0:  cannot open shared object file: No such file or directory
2021-04-19  15:01:33.482886: W  tensorflow/stream_executor/platform/default/dso_loader.cc:55] Could not  load dynamic library 'libcurand.so.10.0'; dlerror: libcurand.so.10.0:  cannot open shared object file: No such file or directory
2021-04-19  15:01:33.482906: W  tensorflow/stream_executor/platform/default/dso_loader.cc:55] Could not  load dynamic library 'libcusolver.so.10.0'; dlerror:  libcusolver.so.10.0: cannot open shared object file: No such file or  directory
2021-04-19 15:01:33.482926: W  tensorflow/stream_executor/platform/default/dso_loader.cc:55] Could not  load dynamic library 'libcusparse.so.10.0'; dlerror:  libcusparse.so.10.0: cannot open shared object file: No such file or  directory
2021-04-19 15:01:33.482946: W  tensorflow/stream_executor/platform/default/dso_loader.cc:55] Could not  load dynamic library 'libcudnn.so.7'; dlerror: libcudnn.so.7: cannot  open shared object file: No such file or directory
```

There are several paths which made lead to a solution:
nvidia-smi shows that cuda 11.2 is installed.
```
sudo find / -name nvcc
```
outputs:
```
/usr/bin/nvcc
/usr/lib/nvidia-cuda-toolkit/bin/nvcc
```

Moreover, there is the path called: /usr/lib/x86_64-linux-gnu
Within that one, there are heaps of files, including some named: "libcudart.so.10.1" and "libcudart.so.10.1.243"

My ~/.zshrc includes those two lines (yes I use zsh):
```
export PATH="$DENO_INSTALL/bin:/usr/lib/nvidia-cuda-toolkit/bin:/usr/lib/x86_64-linux-gnu:$PATH"
export LD_LIBRARY="/usr/lib/nvidia-cuda-toolkit/libdevice:/usr/lib/x86_64-linux-gnu"
```

I am losing control of what is happening here, is there anybody who can explain me how I can fix that mess and stop my computer claiming that Cuda files are missing? I am through nearly all stackoverflow article existing about that subject.

Thank you very much for anybody trying to help me.
Lukas

---

### Post by Xian on 2021-04-20
Do you have the file libcudart.so.11.0 installed locally?

```
sudo apt-get install libcudart11.0
```

```
locate libcudart.so.11.0
/usr/lib/x86_64-linux-gnu/libcudart.so.11.0
```

---

### Post by dorpapst on 2021-04-20
The locate command does not return any path.
It isn't possible to install something like that either, your apt command returns that there is no such package.
But I have installed the toolkit earlier on the computer, where I thought it would contain it:
```
sudo apt install nvidia-cuda-toolkit
```

The only libcudart package I found via apt is one which seems to be already installed:
```
sudo apt-get install libcudart10.1  
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libcudart10.1 is already the newest version (10.1.243-3).
libcudart10.1 set to manually installed.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
```

But when I try to locate this one, it does not return anything either.

---

### Post by Xian on 2021-04-21
What is the output of this command?

```
ls /opt/cuda/targets/x86_64-linux/lib/
```

---

### Post by dorpapst on 2021-04-21
> **Xian said:**
> What is the output of this command?

```
ls /opt/cuda/targets/x86_64-linux/lib/
```

No such file or dictionary.
In fact, there is no cuda folder (or anything like that) in the /opt/ folder.

---

### Post by Xian on 2021-04-21
See if this information is helpful. 

They were missing a different library but the process to resolve may be similar.

[https://medium.com/mlearning-ai/tensorflow-2-4-with-cuda-11-2-gpu-training-fix-87f205215419](https://medium.com/mlearning-ai/tensorflow-2-4-with-cuda-11-2-gpu-training-fix-87f205215419)

---

