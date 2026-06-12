---
title: "[SOLVED] Tboot and Tpm2.0?"
date: 2022-04-01
forum: General Help
---

### Post by tmcca on 2022-04-01
I have Intel TXT and trying to figure out how to use TPM in order for Intel Txt to work?

Do I need to take ownership? Some sort of keys?

I am guessing need to make some sort of policy but how?

I think figured it out need tboot 1.10.5 at least; I will see if it works and give details here

I found one issue have to add SHA256 in cryptographic in Kernel otherwise you will not PCR

Example without in Kernel

/sys/class/tpm/tpm0 will be missing pcr-sha256 directory

here is how I did it:

```
[COLOR=#006600][FONT=Courier]lcp2_mlehash --create --alg sha256 --cmdline "logging=vga,serial,memory" /boot/tboot.gz > mle_hash[/FONT][/COLOR]
[COLOR=#006600][FONT=Courier]lcp2_crtpolelt --create --type mle2 --minver 17 --alg sha256 --out mle.elt mle_hash[/FONT][/COLOR]
[COLOR=#006600][FONT=Courier]# optional PCONF2 element[/FONT][/COLOR]
[COLOR=#006600][FONT=Courier]lcp2_crtpolelt --create --type pconf2 --alg sha256 --pcr0 $(< /sys/class/tpm/tpm0/pcr-sha256/0) --out pcr.elt[/FONT][/COLOR]
[COLOR=#006600][FONT=Courier]# create VErified Launch policy (assuming current kernel is the desired one)[/FONT][/COLOR]
[COLOR=#006600][FONT=Courier]tb_polgen --create --alg sha1 --type continue vl.pol[/FONT][/COLOR]
[COLOR=#006600][FONT=Courier]sudo tb_polgen --add --num 0 --pcr 19 --hash image --cmdline "$(</proc/cmdline) intel_iommu=on noefi" --image "/boot/vmlinuz-$(uname -r)" vl.pol[/FONT][/COLOR]
[COLOR=#006600][FONT=Courier]sudo tb_polgen --add --num 1 --pcr 20 --hash image --image "/boot/initrd.img-$(uname -r)" vl.pol[/FONT][/COLOR]
[COLOR=#006600][FONT=Courier]lcp2_crtpolelt --create --type custom --out vl.elt --uuid tboot vl.pol[/FONT][/COLOR]
[COLOR=#006600][FONT=Courier]# If your PC is recent, listver is probably 0x300[/FONT][/COLOR]
[COLOR=#006600][FONT=Courier]lcp2_crtpollist --create --listver 0x300 --out list_unsig.lst mle.elt pcr.elt vl.elt[/FONT][/COLOR]
[COLOR=#006600][FONT=Courier]# You only need to the next block once. Note TPM 2.0 supports EC keys as well (not shown)[/FONT][/COLOR]
[COLOR=#006600][FONT=Courier]openssl genpkey -out tboot.priv -algorithm rsa[/FONT][/COLOR]
[COLOR=#006600][FONT=Courier]openssl rsa -in tboot.priv -pubout -out tboot.pub[/FONT][/COLOR]
[COLOR=#006600][FONT=Courier]# Sign the list[/FONT][/COLOR]
[COLOR=#006600][FONT=Courier]cp list_unsig.lst list_sig.lst[/FONT][/COLOR]
[COLOR=#006600][FONT=Courier]lcp2_crtpollist --sign --sigalg rsapss --hashalg sha256 --pub tboot.pub --priv tboot.priv --out list_sig.lst[/FONT][/COLOR]
[COLOR=#006600][FONT=Courier]# generate the file we need. Your POLVER may vary.[/FONT][/COLOR]
[COLOR=#006600][FONT=Courier]lcp2_crtpol --create --alg sha256 --polver 3.2 --type list --pol list.pol --data list.data list_sig.lst[/FONT][/COLOR]
[COLOR=#006600][FONT=Courier]# You only need to define and write the policy once[/FONT][/COLOR]
[COLOR=#006600][FONT=Courier]sudo tpm2_nvdefine -s $(( 38 + 32 )) -a 'ownerwrite|policywrite|authread|no_da' 0x1c10106[/FONT][/COLOR]
[COLOR=#006600][FONT=Courier]tpm2_nvwrite -i list.pol 0x1c10106[/FONT][/COLOR]
[COLOR=#006600][FONT=Courier]sudo cp list.data /boot
[/FONT][/COLOR]
```[COLOR=#006600][FONT=Courier]

[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]make new file /etc/default/grub-tboot and set

[/FONT][/COLOR]GRUB_CMDLINE_TBOOT='logging=vga,serial,memory'
GRUB_TBOOT_POLICY_DATA='list.data'

[COLOR=#000000][FONT=Verdana]You may need to add ACM SINIT Module you can get that from 

[/FONT][/COLOR]https://www.intel.com/content/www/us/en/developer/articles/tool/intel-trusted-execution-technology.html
that file goes into /boot
However, I didn't need it since mine is included in BIOS

[COLOR=#000000][FONT=Verdana]sudo update-grub

reboot

check txt-stat and should see 
[/FONT][/COLOR]
TXT-measured launch :TRUE

if not check for ACM module is correct; Check bios make sure INTEL_TXT is enabled under TPM settings

NOTE: first setup you must use TPM_CLEAR and disable INTEL_TXT; do a full system shutdown not reboot and then enable Intel TXT

---

