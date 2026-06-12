---
title: "Ubuntu 7.10 server with xen, domU dies."
date: 2008-01-04
forum: General Help
---

### Post by cableroy on 2008-01-04
Hi

I have installed ubuntu 7.10 server as dom0 with lvm and luks, dom0 is also 7.10 server with 700mb ram, removed /lib/tls and installed libc6-xen i think the package was named
heres the problem:

When i try to sftp  something to the domU the memory gets eaten up as i transfer files if i stop before it has eaten all its ok, this has happend also after several days.
I tried to do a apt-cache search hdparm and it died...

if i don't heres the error:

[  355.036160] ------------[ cut here ]------------
[  355.036176] kernel BUG at /build/buildd/linux-source-2.6.22-2.6.22/debian/build/custom-source-xen/arch/i386/mm/highmem-xen.c:38!
[  355.036188] invalid opcode: 0000 [#8]
[  355.036194] SMP 
[  355.036204] Modules linked in: xt_CONNMARK xt_MARK xt_NFQUEUE ipt_LOG ipt_REJECT ipt_MASQUERADE ipt_REDIRECT xt_connmark xt_helper xt_mac xt_mark xt_limit xt_length xt_tcpudp nfnetlink_queue ip_queue nf_nat_ftp nf_conntrack_ftp xt_state iptable_nat nf_nat nf_conntrack_ipv4 nf_conntrack nfnetlink iptable_filter iptable_mangle ip_tables x_tables af_packet pppoe pppox ppp_generic slhc ipv6 evdev 8139too 3c59x mii ext3 jbd mbcache dm_mirror dm_snapshot dm_mod fuse apparmor commoncap
[  355.036334] CPU:    0
[  355.036335] EIP:    0061:[<c0118462>]    Not tainted VLI
[  355.036337] EFLAGS: 00010202   (2.6.22-14-xen #1)
[  355.036357] EIP is at kmap_atomic_prot+0x172/0x180
[  355.036365] eax: 402d0061   ebx: c1d0d9c0   ecx: 00000000   edx: c1748fb0
[  355.036373] esi: 00000063   edi: 80000000   ebp: 00000007   esp: c1f0fd80
[  355.036381] ds: 007b   es: 007b   fs: 00d8  gs: 0000  ss: 0069
[  355.036389] Process pdflush (pid: 60, ti=c1f0e000 task=c1ee0530 task.ti=c1f0e000)
[  355.036397] Stack: 00000000 ee08b799 c05d76f0 0000002f c1748fb0 00000000 c16e5940 c0876080 
[  355.036425]        c019f851 c0437158 4116b067 00000000 00000e38 c016b1ae 00000063 80000000 
[  355.036450]        c1d0f2e0 c0437158 c174a000 de3b4d88 00000000 c01040dd 00000000 00000000 
[  355.036476] Call Trace:
[  355.036487]  [<ee08b799>] journal_add_journal_head+0x69/0x160 [jbd]
[  355.036515]  [<c019f851>] bio_alloc_bioset+0x81/0x150
[  355.036533]  [<c016b1ae>] page_check_address+0x15e/0x3d0
[  355.036552]  [<c01040dd>] __switch_to+0x23d/0x490
[  355.036568]  [<c016c6ee>] page_mkclean+0x10e/0x240
[  355.036600]  [<c0157b47>] clear_page_dirty_for_io+0x37/0x70
[  355.036613]  [<c0157e23>] write_cache_pages+0x143/0x310
[  355.036628]  [<c0157a30>] __writepage+0x0/0x30
[  355.036642]  [<c01040dd>] __switch_to+0x23d/0x490
[  355.036679]  [<c0158010>] generic_writepages+0x20/0x30
[  355.036693]  [<c0158069>] do_writepages+0x49/0x50
[  355.036707]  [<c01980c3>] __writeback_single_inode+0x93/0x3c0
[  355.036731]  [<c02ff1f6>] schedule+0x356/0x900
[  355.036749]  [<c019877e>] sync_sb_inodes+0x17e/0x240
[  355.036767]  [<c0198c49>] writeback_inodes+0x99/0xd0
[  355.036785]  [<c0158715>] wb_kupdate+0x85/0xf0
[  355.036808]  [<c0158ab0>] pdflush+0x0/0x260
[  355.036818]  [<c0158bf8>] pdflush+0x148/0x260
[  355.036832]  [<c0158690>] wb_kupdate+0x0/0xf0
[  355.036849]  [<c0136312>] kthread+0x42/0x70
[  355.036860]  [<c01362d0>] kthread+0x0/0x70
[  355.036873]  [<c0105927>] kernel_thread_helper+0x7/0x10
[  355.036892]  =======================
[  355.036899] Code: 0c 89 f9 89 f3 25 ff 0f 00 00 30 d2 09 c3 09 d1 89 5c 24 18 89 4c 24 1c e9 4d ff ff ff 83 c4 24 89 d8 5b 5e 5f 5d e9 5e 5c 04 00 <0f> 0b eb fe 0f 0b eb fe 8d b6 00 00 00 00 53 83 ec 08 8b 1d 5c 
[  355.037039] EIP: [<c0118462>] kmap_atomic_prot+0x172/0x180 SS:ESP 0069:c1f0fd80
[  355.037066] note: pdflush[60] exited with preempt_count 1


Now i have to destroy the domU and start it again 

DomU config:

name = "gateway"
disk = [ 'phy:/dev/domu/gateway,sda1,w' ]
vif = [ 'mac=00:01:02:03:04:05, bridge=xenbr0']
#vcpus = [ '2 ' ]
kernel = '/boot/vmlinuz-2.6.22-14-xen'
root = '/dev/sda1 ro'
ramdisk = '/boot/initrd.img-2.6.22-14-xen'
memory = '768'
pci = ['03:09.0','03:0a.0','03:0b.0)']

---

