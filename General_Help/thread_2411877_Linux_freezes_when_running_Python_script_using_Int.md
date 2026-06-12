---
title: "Linux freezes when running Python script using Intel OpenVino, OpenCV VideoCapture an"
date: 2019-02-05
forum: General Help
---

### Post by ts-accessio on 2019-02-05
Hello

We have a difficult to find problem with a Python script, where an  CNN for license plate recognition runs using the Inference Engine. We  are not sure what causes the problem, but the problem started when  upgrading from the alpha version of the Inference Engine to OpenVino  2018R5 in addition with some code changes and an upgrade of Tensorflow.

  Problem description:
  We have a Python script, which runs 3 different CNNs using the  Inference Engine from OpenVino 2018R5 on images from Ethernet cameras,  which are retrieved with OpenCV VideoCapture. In addition ZMQ is used to  pass results to other programs. The used hardware is either an Intel  NUC7BNH, an NUC7DNH or an NUC8BEH (on the NUC8 no freeze was observed  until now). The OS is an Ubuntu 16.04 (with patched kernel  4.7.0.intel.r5.0 or kernel 4.15.0-15-generic (freezes happen less  frequent with kernel 4.15). The script is running multiple times in  separated Docker containers together with programs in other docker  containers.
  What happens is that the Linux freezes randomly after some time  (sometimes after a few minutes, sometimes after a few hours but also two  are now running for many days without a problem). When it freezes no  ACPI shutdown works, the screen freezes and even the Magic SysRq keys  have no effect. A strange side effect is that a lot of network traffic  is created (so much traffic that the network dies and no PC on the  switch can communicate). The logs (kern.log, syslog) show nothing  special.

  If anyone observed a similar problem or has an idea, what can cause this behavior, please let me know.

  Greetings,
  Thomas

---

