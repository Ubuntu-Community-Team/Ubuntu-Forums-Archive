---
title: "Export: Not a valid identifier (Cuda environment setup)"
date: 2019-04-01
forum: General Help
---

### Post by veronica-c on 2019-04-01
Hi I am new to Ubuntu and don't know much about the environment setup. While, after I installed Cuda, I tied to use "nvcc - version" to check whether the installation was successful or not. However, it showed that "nvcc is not found". It happened maybe because I didn't add the path to the ~/.bashrc file. However, when I added the path to the PATH variable as the installation guide ([https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html#post-installation-actions](https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html#post-installation-actions)) shows, it failed.

Part of my ~/.bashrc is :

```
#CUDA


export PATH=/usr/local/cuda-10.1/bin:/usr/local/cuda-10.1/NsightCompute-2019.1${PATH:+:${PATH}}


export LD_LIBRARY_PATH=/usr/local/cuda-10.1/lib64\
                         ${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}






# added by Anaconda2 installer
export PATH="/home/veronica/anaconda2/bin:$PATH"


export CAFFE_ROOT=/home/veronica/caffe
export PYTHONPATH=/home/veronica/caffe/python:/home/veronica/anaconda2/bin/python




# add Bazel path
export PATH="$PATH:$HOME/bin"


export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/lib/nvidia-418


export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/home/veronica/.mujoco/mjpro150/bin

```


But, when I tried to make this file work:

```
$ source ~/.bashrc
bash: export: `:/usr/local/cuda-10.1/lib64:/usr/lib/nvidia-418:/home/veronica/.mujoco/mjpro150/bin': not a valid identifier

```

I am sure these folders all exist.

PS: ":/usr/lib/nvidia-418:/home/veronica/.mujoco/mjpro150/bin" could work well before I added cuda path.

And I tried to change the path to 

```
export PATH=/usr/local/cuda-10.1/bin${PATH:+:${PATH}}
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda-10.1/lib64
```

or
```
export LIBRARY_PATH=$LIBRARY_PATH:/usr/local/cuda-10.1/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
```

No one works.  Please help me. Thank you in advanced!!!

---

### Post by spjackson on 2019-04-02
> **veronica-c said:**
> Hi I am new to Ubuntu and don't know much about the environment setup. While, after I installed Cuda, I tied to use "nvcc - version" to check whether the installation was successful or not. However, it showed that "nvcc is not found". It happened maybe because I didn't add the path to the ~/.bashrc file. However, when I added the path to the PATH variable as the installation guide ([https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html#post-installation-actions](https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html#post-installation-actions)) shows, it failed.

Part of my ~/.bashrc is :

```
#CUDA


export PATH=/usr/local/cuda-10.1/bin:/usr/local/cuda-10.1/NsightCompute-2019.1${PATH:+:${PATH}}


export LD_LIBRARY_PATH=/usr/local/cuda-10.1/lib64\
                         ${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}






# added by Anaconda2 installer
export PATH="/home/veronica/anaconda2/bin:$PATH"


export CAFFE_ROOT=/home/veronica/caffe
export PYTHONPATH=/home/veronica/caffe/python:/home/veronica/anaconda2/bin/python




# add Bazel path
export PATH="$PATH:$HOME/bin"


export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/lib/nvidia-418


export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/home/veronica/.mujoco/mjpro150/bin

```


But, when I tried to make this file work:

```
$ source ~/.bashrc
bash: export: `:/usr/local/cuda-10.1/lib64:/usr/lib/nvidia-418:/home/veronica/.mujoco/mjpro150/bin': not a valid identifier

```

I cannot see anything wrong in what you have actually posted. However, I would expect the error to occur if you had typed "export [COLOR=#ff0000]$[/COLOR]LD_LIBRARY_PATH=stuff"


> 
```
export LIBRARY_PATH=$LIBRARY_PATH:/usr/local/cuda-10.1/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
```

This would not cause the error you are getting but I expect that you want a ":" between lib64 and the following "$".

---

