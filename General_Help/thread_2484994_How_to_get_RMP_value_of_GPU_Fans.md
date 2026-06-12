---
title: "How to get RMP value of GPU Fans?"
date: 2023-03-16
forum: General Help
---

### Post by ricciolino on 2023-03-16
I notice that **psensor** package displayed to me the percentage value of the GPU fans along with its associated RPM value.
I am not able to find a way to obtain that value using any command line tool. I am only able to obtain the percentage value of the speed, but I would like to obtain the _RPM value_ that somehow should be retrieved since **psensor** is able to do that.
I read many post and tried many solutions, but no one of those help me.
I see [this]("https://www.reddit.com/r/nvidia/comments/kdjdjz/nvidiasmi_linux_how_to_get_fan_rpm_not_speed/") post.
I try with [this]("https://pypi.org/project/nvidia-ml-py/") python module.

No way to get RPM values.

*OS*: **Ubuntu 22.04**
*GPU*: **Nvidia RTX 3080**

Any help ?

_________________
| SOLUTION --> [#6]("https://ubuntuforums.org/showthread.php?t=2484994&p=14135313#post14135313")  |[URL="https://ubuntuforums.org/showthread.php?t=2484994&p=14135313#post14135313"]
[/URL]-----------------------------

---

### Post by MAFoElffen on 2023-03-16
Uisng the NVidia NVML API library: [https://docs.nvidia.com/deploy/nvml-api/group__nvmlDeviceQueries.html#group__nvmlDeviceQueries_1ge8e3e5b5b9dcf436e4537982cf647d4e](https://docs.nvidia.com/deploy/nvml-api/group__nvmlDeviceQueries.html#group__nvmlDeviceQueries_1ge8e3e5b5b9dcf436e4537982cf647d4e)

---

### Post by ricciolino on 2023-03-17
I already tried through it.

But with the API you linked I only get the percentage value.

I also saw the **nvmlUnitGetFanSpeedInfo** API in [this]("https://developer.download.nvidia.com/compute/cuda/5_5/rel/nvml/nvml.5.319.43.pdf") document that should return the RPM value using the [structnvmlUnitFanInfo__t]("https://docs.nvidia.com/deploy/nvml-api/structnvmlUnitFanInfo__t.html#structnvmlUnitFanInfo__t") structure, anyway it doesn't work for me.

Here is my snippet of code:
[FONT=courier new]
#!/usr/bin/python3

import os
import sys
from pynvml import *

nvmlInit()
handle = nvmlDeviceGetHandleByIndex(0)

try:
     (info) = nvmlUnitGetFanSpeedInfo(handle)
     print(info.speed)
except NVMLError as error:
     print(error)

nvmlShutdown()

sys.exit(0)
[/FONT]
It raise the "**Invalid Argument**" exception:[FONT=courier new]

> python3 get_RPM_GPU_fans.py
Invalid Argument[/FONT]

---

### Post by MAFoElffen on 2023-03-17
With pynvml, users where getting errors with that. But others helping them solve those errors reported that if they instead used py3nvml, that the below code worked for them:
```

import py3nvml
pynvml.nvmlInit()
h = [pynvml.nvmlDeviceGetHandleByIndex(i) for i in range(pynvml.nvmlDeviceGetCount())]
pynvml.nvmlDeviceGetFanSpeedInfo(h[0])


```
RE: [https://docs.nvidia.com/deploy/nvml-api/group__nvmlUnitQueries.html#group__nvmlUnitQueries_1gf8d512cb5764d671c8bd6b0ef32ae456](https://docs.nvidia.com/deploy/nvml-api/group__nvmlUnitQueries.html#group__nvmlUnitQueries_1gf8d512cb5764d671c8bd6b0ef32ae456)

The big reason why you are getting that error is this, from the requirements section of pynvml: [https://pythonhosted.org/nvidia-ml-py/](https://pythonhosted.org/nvidia-ml-py/)
> 

REQUIRES

Python 2.5, or an earlier version with the ctypes module.

Python version 2, not Python3... py3nvml supports Python3... RE: [https://morioh.com/p/bbfe67a3d034](https://morioh.com/p/bbfe67a3d034)

I then found a python class written for py3nvml: (starts at line #165)
[https://github.com/mark9064/system_metrics_influx/blob/master/system_metrics_influx.py#L165](https://github.com/mark9064/system_metrics_influx/blob/master/system_metrics_influx.py#L165)

I hope those examples and using the correct modules for Python3 help you...

---

### Post by ricciolino on 2023-03-17
@MAFoElffen I really appreciate your responses trying to give me an help, thank you!
I install py3nvml version for a python3 compatible module, but...

> **MAFoElffen said:**
> ...that the below code worked for them:
```

import py3nvml
pynvml.nvmlInit()
h = [pynvml.nvmlDeviceGetHandleByIndex(i) for i in range(pynvml.nvmlDeviceGetCount())]
pynvml.nvmlDeviceGetFanSpeedInfo(h[0])


```

Unfortunately still this code doesn't not work for me.

Executing exactly that snippet, I got this output:

```

Traceback (most recent call last):
  File "/home/ricciolino/Desktop/tmp/./bla", line 6, in <module>
    pynvml.nvmlInit()
NameError: name 'pynvml' is not defined. Did you mean: 'py3nvml'?

```

So I rearranged a little bit to make it execute fine (note that **nvmlDeviceGetFanSpeedInfo** does not exist, do exists either **nvmlDeviceGetFanSpeed**, that returns the fan speed percentage values, or **nvmlUnitGetFanSpeedInfo**, that, as per the documentation, should return the RPM value of the fans). Here is the rearranged script.

```

#!/usr/bin/python3

import os
import sys
from py3nvml import *
py3nvml.nvmlInit()
h = [py3nvml.nvmlDeviceGetHandleByIndex(i) for i in range(py3nvml.nvmlDeviceGetCount())]
print(py3nvml.nvmlUnitGetFanSpeedInfo(h[0]))
py3nvml.nvmlShutdown()
print("CIAO")
sys.exit(0)

```

but I got:

```

Traceback (most recent call last):
  File "/home/ricciolino/Desktop/tmp/./bla", line 8, in <module>
    print(py3nvml.nvmlUnitGetFanSpeedInfo(h[0]))
  File "/home/ricciolino/.local/lib/python3.10/site-packages/py3nvml/py3nvml.py", line 1633, in nvmlUnitGetFanSpeedInfo
    _nvmlCheckReturn(ret)
  File "/home/ricciolino/.local/lib/python3.10/site-packages/py3nvml/py3nvml.py", line 719, in _nvmlCheckReturn
    raise NVMLError(ret)
py3nvml.py3nvml.NVMLError_InvalidArgument: Invalid Argument

```

So still the same **Invalid Argument** error...

> **MAFoElffen said:**
> With pynvml, users where getting errors with  that. But others helping them solve those errors reported that if they  instead used **py3nvml**, that the below code worked for them:
I then found a python class written for py3nvml: (starts at line #165)

I check it but even in that example the class only use the **nvmlDeviceGetFanSpeed** API to retrieve the percentage value of the fan speeds. I am not interested in this value. I need the RPM values.

---

### Post by ricciolino on 2023-03-17
I finally found a way to query my GPU for getting RPM fan values.
I made reverse engineering over the **psensor** source code and I wrote this simple C code snippet to get the RPM value of a specific fan of the GPU (passing 0 or 1 as identifier to the binary).

Here is my **get_GPU_fan_RPM_values.c** script:

```

#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>
#include <X11/Xlib.h>
#include <NVCtrl/NVCtrl.h>
#include <NVCtrl/NVCtrlLib.h>

static Display *display;

static double get_att(int target, int id, int att)
{
    Bool res;
    int temp;

    res = XNVCTRLQueryTargetAttribute(display, target, id, 0, att, &temp);

    if (res == True)
        return temp;

    return -1;
}

void nvidia_cleanup(void)
{
    if (display) {
        XCloseDisplay(display);
        display = NULL;
    }
}

bool isFanId(char number[])
{
    int i = 0;
    if (number[0] == '-')
        return false;
    for (; number[i] != 0; i++)
    {
        if (number[i] > '1' || number[i] < '0')
            return false;
    }
    return true;
}

int main(int argc, char** argv) {

    if ( !(argc == 2) ) return 1;
    if ( !isFanId(argv[1]) ) return 1;

    int fanId = atoi(argv[1]);

    display = XOpenDisplay(NULL);

    if (!display) {
        printf("Cannot open connection to X11 server\n");
        nvidia_cleanup();
        return 1;
    }

    int evt, err;
    if (!XNVCTRLQueryExtension(display, &evt, &err)) {
        printf("XNVCTRLQueryExtension error %d (evt %d)\n", err, evt);
        nvidia_cleanup();
        return 1;
    }

    printf("%d\n", (int)get_att(NV_CTRL_TARGET_TYPE_COOLER, 1, NV_CTRL_THERMAL_COOLER_SPEED));
    //printf("fan %d: %d RPM\n", fanId, (int)get_att(NV_CTRL_TARGET_TYPE_COOLER, 1, NV_CTRL_THERMAL_COOLER_SPEED));

    nvidia_cleanup();
    
    return 0;
}

```

Compile it with:

```
[FONT=courier new]gcc -o get_GPU_fan_RPM_values get_GPU_fan_RPM_values.c -lX11 -lXNVCtrl[/FONT]
```

Execute it like this:

 ```
[FONT=courier new]./get_GPU_fan_RPM_values 0[/FONT]
```
[SIZE=1]*or*[/SIZE]
 ```
[FONT=courier new]./get_GPU_fan_RPM_values 1[/FONT]
```

---

### Post by MAFoElffen on 2023-03-18
Looks good.

Sorry. Been a very long day, Just got home from work. It's 2 am here.

If solved, please go to the "Thread Tools" link at the upper right of this page, and mark it Solved.

---

### Post by ricciolino on 2023-03-19
> **MAFoElffen said:**
> Sorry. Been a very long day, Just got home from work. It's 2 am here.
Don't worry at all, in fact thanks for the replies and advice.

> **MAFoElffen said:**
> If solved, please go to the "Thread Tools" link at the upper right of this page, and mark it Solved.
Will do!

---

