---
title: "Audio and Microphone in KVM with Win10 on Ubuntu 22.04"
date: 2024-12-02
forum: General Help
---

### Post by agonzalesc on 2024-12-02
Hi,
I have Win 10 running in KVM/QEMU correctly on my Ubuntu 22.04, for this I have used Virtio drivers.


Although the volume is active and can be manipulated in Win10, it does not actually sound in my headphones or my PC and I understand that this happens because it is a virtual machine.


I have followed these steps to try to activate it, without success:

[https://getlabsdone.com/kvm-windows-no-sound-lets-fix-it/](https://getlabsdone.com/kvm-windows-no-sound-lets-fix-it/)
[https://gurjeet-tech.blogspot.com/2012/09/how-to-install-kvm-with-working-audio.html](https://gurjeet-tech.blogspot.com/2012/09/how-to-install-kvm-with-working-audio.html)



The result has been that now in Win10, it says "no device found" in the sound and I cannot even manipulate the volume.






Could you give me more ideas to continue investigating please?

---

### Post by TheFu on 2024-12-04
Did you pass the USB devices through to the VM for exclusive use?  That should be it.  virt-manager makes doing this pretty easy.  You just need to select the USB devices from a list.

Now, if either the mic or speakers aren't USB connected, IDK. Sorry.  USB passthru has worked well in libvirt for a long time.  I've never tried to passthru analog audio.

And I don't have win10/11.

---

### Post by 1fallen on 2024-12-04
> **agonzalesc said:**
> Hi,

Although the volume is active and can be manipulated in Win10, it does not actually sound in my headphones or my PC and I understand that this happens because it is a virtual machine.


I have followed these steps to try to activate it, without success:

[https://getlabsdone.com/kvm-windows-no-sound-lets-fix-it/](https://getlabsdone.com/kvm-windows-no-sound-lets-fix-it/)
[https://gurjeet-tech.blogspot.com/2012/09/how-to-install-kvm-with-working-audio.html](https://gurjeet-tech.blogspot.com/2012/09/how-to-install-kvm-with-working-audio.html)



The result has been that now in Win10, it says "no device found" in the sound and I cannot even manipulate the volume.






Could you give me more ideas to continue investigating please?

Interesting this is my settings for the KVM
```
<sound model="ich9">
  <address type="pci" domain="0x0000" bus="0x00" slot="0x1b" function="0x0"/>
</sound>


```
That's found in the XML config. I have no issues using that setting. from just speakers to a headphone connected to the laptop.
No additional steps needed on my end.

Sorry I missed this post earlier.

---

### Post by agonzalesc on 2024-12-04
Hi @TheFu
Thanks for your reply.

Yes! To install win 10 in my KVM I use this guide : [https://getlabsdone.com/install-windows-10-on-ubuntu-kvm/](https://getlabsdone.com/install-windows-10-on-ubuntu-kvm/)

I installed virtio drivers and Spice Guest Tools, But that is not heard in my headphones or on the PC speakers 

Regards

---

### Post by 1fallen on 2024-12-04
Can you show me your current settings, please see my screenshots.

---

### Post by agonzalesc on 2024-12-04
Hi @1fallen
Thanks for your reply.

I left everything as before and only changed to ICH9 for sound (previously it was AC97), and the volume can be manipulated but nothing can be heard on my speakers.

[IMG]https://blog.letsgodev.com/wp-content/uploads/2024/12/qemu1.png[/IMG]

[IMG]https://blog.letsgodev.com/wp-content/uploads/2024/12/qemu2.png[/IMG]


[IMG]https://blog.letsgodev.com/wp-content/uploads/2024/12/qemu3.png[/IMG]


As you can see in my attached images, I can manipulate the volume, but that's it, it's silent.

Thanks

---

### Post by tea for one on 2024-12-05
In your xml screenshot, you have <alias name="sound0"/>
Perhaps remove it and try this setting
```
<sound model="ich9">
  <address type="pci" domain="0x0000" bus="0x00" slot="0x1b" function="0x0"/>
</sound>
```

---

### Post by TheFu on 2024-12-05
Just tested this here.  Copied into the Win7 VM a video and double-clicked to start it.  VLC started up and it played fine.  The default AC97 sound was setup in the VM.  No USB involved.

The host system is Ubuntu 20.04 server with 3.5mm analog stereo audio out plugged into the back of the Asus ROG STRIX B450-F GAMING motherboard with a Ryzen 5600G APU.  The APU isn't involved in audio, except over HDMI, which I don't use.

I didn't setup anything special. It "just worked".  This VM is old and has been migrated to new VM hosts at least 3 times.  At boot, I hear the "Win7 Chimes" every time. I'd forgotten about that.  This VM is only around for 2 programs I still use.

In the virt-manager settings related to video+sound, there's just 
[LIST]
[*]Display Spice
[*]Sound ac97
[*]Channel spice
[*]Video QXL
[/LIST]

My NIC was virtio, but then there was a boot issue and the RH virtio drivers weren't available, so I switched back to the Intel PRO/1000, e1000, driver.  Win7 didn't include virtio, so the boot recovery was always a hassle.  I am using virtio for storage, however.  It has probably been 15 yrs since I setup this VM.  I know I stopped patching it around 2015, when MSFT changed their EULA to container clauses to which I didn't agree.  They really tried to force those changes onto us. I was forced to firewall at my network layer much of MSFT internet addresses.  I'd already been blocking their corporate network from accessing my public subnet after a number of hacking attempts (weak attempts, probably a bad actor hacked MSFT and was jumping from their network to the rest of the world).

Anyway, it just works here.  I'm not running Ubuntu 22.04 nor do I have (or will I ever have Win8 or newer).  I'm fortunate to be in a place of my life where I don't need and will never need MS-Windows before I die.

---

### Post by agonzalesc on 2024-12-05
Hi. Thanks for your reply.


Before starting Windows, this is my xml.

```
<sound model="ich9">
  <address type="pci" domain="0x0000" bus="0x00" slot="0x1b" function="0x0"/>
</sound>

```



But after starting Windows, that alias is added and this is the xml. I have deleted it but when I turn it on again, it appears.


```
<sound model="ich9">
  <alias name="sound0"/>
  <address type="pci" domain="0x0000" bus="0x00" slot="0x1b" function="0x0"/>
</sound>

```


I followed this tutorial to the letter to install Win10 with Virtio : [https://getlabsdone.com/install-windows-10-on-ubuntu-kvm/](https://getlabsdone.com/install-windows-10-on-ubuntu-kvm/)


Thanks.

---

### Post by TheFu on 2024-12-05
I don't think virtio is needed for audio - or involved.

There isn't 1 virtio.  There are 3.
Storage
Network
Graphics

My libvirt is too old to support GPU virtio, so I still use Spice and spice channels.
Inside the "defined" XML for the VM are these lines (just adding to the collection):
```
    <sound model='ac97'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </sound>
    <video>
      <model type='qxl' ram='65536' vram='65536' vgamem='16384' heads='1' primary='yes'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x0a' function='0x0'/>
    </video>
```
The VM is running now and as I grabbed those lines. I didn't manually modify the XML.  If you do, then you'll need to use the **virsh edit** command, to ensure the updates are "defined" too.  I think that just copies the XML file from /etc/... to /var/ somewhere. I don't keep up with that stuff, since I've never needed know know, even when manually migrating VMs to different hosts, which I've done many times.

---

### Post by 1fallen on 2024-12-05
My Windows 10 did not like 'ac97' at all....Sound was Crossed out after that change.

"ich9" Was the best option for mine.

---

### Post by agonzalesc on 2024-12-06
Hi.
This is my general config XML

```
<domain type="kvm">
  <name>win10</name>
  <uuid>27a4d09d-d1b8-4b03-93b0-d8983665398c</uuid>
  <metadata>
    <libosinfo:libosinfo xmlns:libosinfo="http://libosinfo.org/xmlns/libvirt/domain/1.0">
      <libosinfo:os id="http://microsoft.com/win/10"/>
    </libosinfo:libosinfo>
  </metadata>
  <memory unit="KiB">8290304</memory>
  <currentMemory unit="KiB">8290304</currentMemory>
  <vcpu placement="static">4</vcpu>
  <os>
    <type arch="x86_64" machine="pc-q35-6.2">hvm</type>
    <bootmenu enable="yes"/>
  </os>
  <features>
    <acpi/>
    <apic/>
    <hyperv mode="custom">
      <relaxed state="on"/>
      <vapic state="on"/>
      <spinlocks state="on" retries="8191"/>
    </hyperv>
    <vmport state="off"/>
  </features>
  <cpu mode="host-passthrough" check="none" migratable="on">
    <topology sockets="1" dies="1" cores="2" threads="2"/>
  </cpu>
  <clock offset="localtime">
    <timer name="rtc" tickpolicy="catchup"/>
    <timer name="pit" tickpolicy="delay"/>
    <timer name="hpet" present="no"/>
    <timer name="hypervclock" present="yes"/>
  </clock>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>destroy</on_crash>
  <pm>
    <suspend-to-mem enabled="no"/>
    <suspend-to-disk enabled="no"/>
  </pm>
  <devices>
    <emulator>/usr/bin/qemu-system-x86_64</emulator>
    <disk type="file" device="disk">
      <driver name="qemu" type="qcow2" discard="unmap"/>
      <source file="/var/lib/libvirt/images/win10.qcow2"/>
      <target dev="vda" bus="virtio"/>
      <boot order="2"/>
      <address type="pci" domain="0x0000" bus="0x04" slot="0x00" function="0x0"/>
    </disk>
    <disk type="file" device="cdrom">
      <driver name="qemu" type="raw"/>
      <target dev="sdb" bus="sata"/>
      <readonly/>
      <boot order="1"/>
      <address type="drive" controller="0" bus="0" target="0" unit="1"/>
    </disk>
    <disk type="file" device="cdrom">
      <driver name="qemu" type="raw"/>
      <target dev="sdc" bus="sata"/>
      <readonly/>
      <boot order="3"/>
      <address type="drive" controller="0" bus="0" target="0" unit="2"/>
    </disk>
    <controller type="usb" index="0" model="qemu-xhci" ports="15">
      <address type="pci" domain="0x0000" bus="0x02" slot="0x00" function="0x0"/>
    </controller>
    <controller type="pci" index="0" model="pcie-root"/>
    <controller type="pci" index="1" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="1" port="0x10"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x02" function="0x0" multifunction="on"/>
    </controller>
    <controller type="pci" index="2" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="2" port="0x11"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x02" function="0x1"/>
    </controller>
    <controller type="pci" index="3" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="3" port="0x12"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x02" function="0x2"/>
    </controller>
    <controller type="pci" index="4" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="4" port="0x13"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x02" function="0x3"/>
    </controller>
    <controller type="pci" index="5" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="5" port="0x14"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x02" function="0x4"/>
    </controller>
    <controller type="pci" index="6" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="6" port="0x15"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x02" function="0x5"/>
    </controller>
    <controller type="pci" index="7" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="7" port="0x16"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x02" function="0x6"/>
    </controller>
    <controller type="pci" index="8" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="8" port="0x17"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x02" function="0x7"/>
    </controller>
    <controller type="pci" index="9" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="9" port="0x18"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x03" function="0x0" multifunction="on"/>
    </controller>
    <controller type="pci" index="10" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="10" port="0x19"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x03" function="0x1"/>
    </controller>
    <controller type="pci" index="11" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="11" port="0x1a"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x03" function="0x2"/>
    </controller>
    <controller type="pci" index="12" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="12" port="0x1b"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x03" function="0x3"/>
    </controller>
    <controller type="pci" index="13" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="13" port="0x1c"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x03" function="0x4"/>
    </controller>
    <controller type="pci" index="14" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="14" port="0x1d"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x03" function="0x5"/>
    </controller>
    <controller type="pci" index="15" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="15" port="0x1e"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x03" function="0x6"/>
    </controller>
    <controller type="pci" index="16" model="pcie-to-pci-bridge">
      <model name="pcie-pci-bridge"/>
      <address type="pci" domain="0x0000" bus="0x06" slot="0x00" function="0x0"/>
    </controller>
    <controller type="sata" index="0">
      <address type="pci" domain="0x0000" bus="0x00" slot="0x1f" function="0x2"/>
    </controller>
    <controller type="virtio-serial" index="0">
      <address type="pci" domain="0x0000" bus="0x03" slot="0x00" function="0x0"/>
    </controller>
    <interface type="network">
      <mac address="52:54:00:47:77:79"/>
      <source network="default"/>
      <model type="virtio"/>
      <address type="pci" domain="0x0000" bus="0x01" slot="0x00" function="0x0"/>
    </interface>
    <serial type="pty">
      <target type="isa-serial" port="0">
        <model name="isa-serial"/>
      </target>
    </serial>
    <console type="pty">
      <target type="serial" port="0"/>
    </console>
    <channel type="spicevmc">
      <target type="virtio" name="com.redhat.spice.0"/>
      <address type="virtio-serial" controller="0" bus="0" port="1"/>
    </channel>
    <input type="tablet" bus="usb">
      <address type="usb" bus="0" port="1"/>
    </input>
    <input type="mouse" bus="ps2"/>
    <input type="keyboard" bus="ps2"/>
    <graphics type="spice" autoport="yes">
      <listen type="address"/>
      <image compression="off"/>
    </graphics>
    <graphics type="vnc" port="-1" autoport="yes">
      <listen type="address"/>
    </graphics>
    <sound model="ich9">
      <address type="pci" domain="0x0000" bus="0x00" slot="0x1b" function="0x0"/>
    </sound>
    <audio id="1" type="none"/>
    <video>
      <model type="qxl" ram="65536" vram="65536" vgamem="16384" heads="1" primary="yes"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x01" function="0x0"/>
    </video>
    <redirdev bus="usb" type="spicevmc">
      <address type="usb" bus="0" port="2"/>
    </redirdev>
    <redirdev bus="usb" type="spicevmc">
      <address type="usb" bus="0" port="3"/>
    </redirdev>
    <memballoon model="virtio">
      <address type="pci" domain="0x0000" bus="0x05" slot="0x00" function="0x0"/>
    </memballoon>
  </devices>
</domain>

```

I use KVM only for making videos in Filmora or Capcut, both of which have not worked for me with Wine. It's funny because I always run into a new problem when I'm close to it.


I appreciate the help, I'll keep googling to see what else I can find and if I find the solution I'll write it here.

Thanks

---

### Post by TheFu on 2024-12-06
I would suggest following the normal method of simplifying and testing, repeat.  If you aren't using USB passthru, remove those options.  If you aren't using CDROMs, remove them.  Simplify the VM.  Fewer things inside it, fewer things to muck up the works.

I've never used balloon memory. Do you need it? If not, disable/remove it.

Simplify.

---

