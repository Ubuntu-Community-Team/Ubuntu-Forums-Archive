---
title: "Problems Connecting Samsung Galaxy S3 to Ubuntu"
date: 2012-12-04
forum: General Help
---

### Post by Jonners59 on 2012-12-04
I am trying to connect my Samsung SIII to my PC.  I have tracked down that gMTP is the app, and that I need to set the device to "Media Device" (MTP), but I can not get it to connect.

The SIII is up to date and rooted
The PC is running 12:10 64-bit and up to date

Log enclosed
[HTML]
Starting program: /usr/bin/gmtp 
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".
[New Thread 0x7fffeea21700 (LWP 19522)]
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 9: reading configurations from ~/.fonts.conf is deprecated.
[New Thread 0x7fffecd5c700 (LWP 19523)]
[New Thread 0x7fffe5c06700 (LWP 19524)]
Device 0 (VID=04e8 and PID=6860) is a Samsung GT P7310/P7510/N7000/I9070/I9100/I9300 Galaxy Tab 7.7/10.1/S2/S3/Nexus/Note/Y.
PTP_ERROR_IO: failed to open session, trying again after resetting USB interface
LIBMTP libusb: Attempt to reset device
inep: usb_get_endpoint_status(): No such device
outep: usb_get_endpoint_status(): No such device
usb_clear_halt() on IN endpoint: No such device
usb_clear_halt() on OUT endpoint: No such device
usb_clear_halt() on INTERRUPT endpoint: No such device
usb_open(): No such device
LIBMTP PANIC: Could not init USB on second attempt
Detect: Unable to open raw device?
LIBMTP PANIC: Trying to dump the error stack of a NULL device!
LIBMTP PANIC: Trying to clear the error stack of a NULL device!
Device 0 (VID=04e8 and PID=6860) is a Samsung GT P7310/P7510/N7000/I9070/I9100/I9300 Galaxy Tab 7.7/10.1/S2/S3/Nexus/Note/Y.
[Thread 0x7fffecd5c700 (LWP 19523) exited]
[New Thread 0x7fffecd5c700 (LWP 24196)]
[Thread 0x7fffecd5c700 (LWP 24196) exited]

Program received signal SIGINT, Interrupt.
0x00007ffff5cb2303 in poll () from /lib/x86_64-linux-gnu/libc.so.6
(gdb) backtrace full
#0  0x00007ffff5cb2303 in poll () from /lib/x86_64-linux-gnu/libc.so.6
No symbol table info available.
#1  0x00007ffff2c47113 in ?? () from /lib/x86_64-linux-gnu/libusb-1.0.so.0
No symbol table info available.
#2  0x00007ffff2c47d87 in libusb_handle_events_timeout_completed () from /lib/x86_64-linux-gnu/libusb-1.0.so.0
No symbol table info available.
#3  0x00007ffff2c47e50 in libusb_handle_events_completed () from /lib/x86_64-linux-gnu/libusb-1.0.so.0
No symbol table info available.
#4  0x00007ffff2c485c9 in ?? () from /lib/x86_64-linux-gnu/libusb-1.0.so.0
No symbol table info available.
#5  0x00007ffff2c48994 in libusb_bulk_transfer () from /lib/x86_64-linux-gnu/libusb-1.0.so.0
No symbol table info available.
#6  0x00007ffff68446b3 in ptp_write_func (size=size@entry=16, data=0xb6b9b0, written=written@entry=0x7fffffffcf18, handler=0x7fffffffcf20, handler=0x7fffffffcf20) at libusb1-glue.c:970
        usbwritten = <optimised out>
        xwritten = 0
        getfunc_ret = <optimised out>
        ptp_usb = 0xb6b9b0
        towrite = 16
        ret = 0
        curwrite = 0
        bytes = 0xba0f20 "\020"
#7  0x00007ffff6845618 in ptp_usb_sendreq (params=0xb62730, req=0x7fffffffd2e0) at libusb1-glue.c:1160
        ret = <optimised out>
        usbreq = {length = 16, type = 1, code = 4098, trans_id = 0, payload = {params = {param1 = 1, param2 = 0, param3 = 0, param4 = 0, param5 = 0}, data = "\001", '\000' <repeats 19 times>"\240, =\226\365\377\177\000\000\310\000\000\000\000\000\000\000\000\217\212\000\000\000\000\000\260\271\266\000\000\000\000\000 \230\253\000\000\000\000\000\260\242\266\000\000\000\000\000\266\000\000\000\000\000p)\266", '\000' <repeats 21 times>, "p)\266", '\000' <repeats 13 times>, "\266", '\000' <repeats 13 times>, "\001\000\000\000\000\000\000\000}?\304\362\377\177\000\000\260\321\377\377\377\177\000\000 \000\000\000\060\000\000\000\300\321\377\377\377\177\000\000\000\321\377\377\377\177\000\000\260/\264\000\000\000\000\000\220\241\266", '\000' <repeats 13 times>, "=", '\000' <repeats 23 times>, "L\000\000\000\000\000\000\000\227v\304\362\377\177\000\000\266\000\000\000\000\000 \230\253\000\000\000\000\000\030\231\253\000\000\000\000\000\326I\304\362\377\177", '\000' <repeats 11 times>, "-\340\t\374j\355\001 \230\253\000\000\000\000\000a\217\304\362\377\177\000\000 \230\253\000\000\000\000\000"...}}
        memhandler = {getfunc = 0x7ffff6842ec0 <memory_getfunc>, putfunc = 0x7ffff6843550 <memory_putfunc>, priv = 0xa012a0}
        written = 0
        towrite = 16
        txt = "Open session\000\000\000\000\220 \256\000\000\000\000\000\004\000\000\000\000\000\000\000\020\320\377\377\377\177\000\000\060\000\000\000\000\000 \230\253\000\000\000\000\000\220 \256\000\000\000\000\000\375\377\377\377\000\000\000\000\375\377\377\377\000\000\000\000\020\320\377\377\377\177\000\000\336O\304\362\377\177\000\000\375\377\377\377", '\000' <repeats 12 times>, "\022\001\020\001\000\000\000\b\000\000\000\000\000\000\000\000\220 \256\000\000\000\000\000\t\000\000\000\000\000\000\000\220 \256\000\000\000\000\000\a\000\000\000\000\000\000\000\020\204b\000\000\000\000\000%L\204\366\377\177\000\000\000\201\212\000\000\000\000\000\252\366\377\177\000\000 8\226\365\377\177\000\000\000\000\000\000\000\000\000\000`\343\237\000\000\000\000\000\340\005f\000\000\000\000\000\022\001\020\001\000\000\000\bm\004\330\b\000\001\000\000\000\001i\000\000\000\000\000X\245\252\366\377\177\000"
        __FUNCTION__ = "ptp_usb_sendreq"
#8  0x00007ffff6835de8 in ptp_transaction_new (handler=<optimised out>, sendlen=<optimised out>, flags=<optimised out>, ptp=0x7fffffffd2e0, params=0xb62730) at ptp.c:152
        r = <optimised out>
        tries = <optimised out>
        cmd = 4098
#9  ptp_transaction_new (params=0xb62730, ptp=0x7fffffffd2e0, flags=<optimised out>, sendlen=<optimised out>, handler=<optimised out>) at ptp.c:138
No locals.
#10 0x00007ffff6836d5e in ptp_opensession (params=params@entry=0xb62730, session=session@entry=1) at ptp.c:541
        ret = 65020
        ptp = {Code = 4098, SessionID = 0, Transaction_ID = 0, Param1 = 1, Param2 = 0, Param3 = 0, Param4 = 0, Param5 = 0, Nparam = 1 '\001'}
#11 0x00007ffff6846844 in configure_usb_device (device=device@entry=0x9dd8e0, params=params@entry=0xb62730, usbinfo=usbinfo@entry=0xb4aad0) at libusb1-glue.c:1992
        ptp_usb = 0xb6b9b0
        ldevice = 0xb6a2b0
        ret = <optimised out>
        found = 1
        i = <optimised out>
        nrofdevs = <optimised out>
        devs = 0xb8df30
        desc = {bLength = 18 '\022', bDescriptorType = 1 '\001', bcdUSB = 512, bDeviceClass = 0 '\000', bDeviceSubClass = 0 '\000', bDeviceProtocol = 0 '\000', bMaxPacketSize0 = 64 '@', idVendor = 1256, idProduct = 26720, bcdDevice = 1024, iManufacturer = 2 '\002', iProduct = 3 '\003', iSerialNumber = 4 '\004', bNumConfigurations = 1 '\001'}
        __FUNCTION__ = "configure_usb_device"
#12 0x00007ffff682b491 in LIBMTP_Open_Raw_Device_Uncached (rawdevice=0x9dd8e0) at libmtp.c:1860
        mtp_device = 0xb4aac0
        bs = 0 '\000'
        current_params = 0xb62730
        ptp_usb = <optimised out>
        err = <optimised out>
        i = <optimised out>
        __FUNCTION__ = "LIBMTP_Open_Raw_Device_Uncached"
#13 0x00007ffff682c106 in LIBMTP_Open_Raw_Device (rawdevice=<optimised out>) at libmtp.c:2077
        mtp_device = <optimised out>
#14 0x000000000040a02c in ?? ()
No symbol table info available.
#15 0x000000000041b73b in ?? ()
No symbol table info available.
#16 0x00007ffff6f6e140 in g_closure_invoke (closure=0x8c1490, return_value=0x0, n_param_values=1, param_values=0x7fffffffd730, invocation_hint=0x7fffffffd6d0) at /build/buildd/glib2.0-2.34.0/./gobject/gclosure.c:777
        marshal = 0x7ffff6f6ff70 <g_cclosure_marshal_VOID__VOID>
        marshal_data = 0x0
        in_marshal = 0
        real_closure = 0x8c1470
        __PRETTY_FUNCTION__ = "g_closure_invoke"
#17 0x00007ffff6f7f550 in signal_emit_unlocked_R (node=node@entry=0x64cd30, detail=detail@entry=0, instance=instance@entry=0x7cd000, emission_return=emission_return@entry=0x0, instance_and_params=instance_and_params@entry=0x7fffffffd730) at /build/buildd/glib2.0-2.34.0/./gobject/gsignal.c:3551
        tmp = <optimised out>
        handler = 0x8c0730
        accumulator = 0x0
        emission = {next = 0x7fffffffdcf0, instance = 0x7cd000, ihint = {signal_id = 76, detail = 0, run_type = G_SIGNAL_RUN_FIRST}, state = EMISSION_RUN, chain_type = 4}
        class_closure = 0x64ccb0
        hlist = 0x8c0730
        handler_list = 0x8c0730
        return_accu = 0x0
        accu = {g_type = 0, data = {{v_int = 0, v_uint = 0, v_long = 0, v_ulong = 0, v_int64 = 0, v_uint64 = 0, v_float = 0, v_double = 0, v_pointer = 0x0}, {v_int = 0, v_uint = 0, v_long = 0, v_ulong = 0, v_int64 = 0, v_uint64 = 0, v_float = 0, v_double = 0, v_pointer = 0x0}}}
        signal_id = 76
        max_sequential_handler_number = 3121
        return_value_altered = 1
#18 0x00007ffff6f874af in g_signal_emit_valist (instance=0x7cd000, signal_id=<optimised out>, detail=0, var_args=var_args@entry=0x7fffffffd978) at /build/buildd/glib2.0-2.34.0/./gobject/gsignal.c:3300
        instance_and_params = 0x7fffffffd730
        signal_return_type = 4
        param_values = 0x7fffffffd748
        node = 0x64cd30
        i = <optimised out>
        n_params = 0
        __PRETTY_FUNCTION__ = "g_signal_emit_valist"
#19 0x00007ffff6f87642 in g_signal_emit (instance=<optimised out>, signal_id=<optimised out>, detail=<optimised out>) at /build/buildd/glib2.0-2.34.0/./gobject/gsignal.c:3356
        var_args = {{gp_offset = 24, fp_offset = 48, overflow_arg_area = 0x7fffffffda50, reg_save_area = 0x7fffffffd990}}
#20 0x00007ffff79de04c in gtk_widget_activate () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
No symbol table info available.
#21 0x00007ffff78cdbfe in gtk_menu_shell_activate_item () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
No symbol table info available.
#22 0x00007ffff78cdf9b in ?? () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
No symbol table info available.
#23 0x00007ffff78afaaf in ?? () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
No symbol table info available.
#24 0x00007ffff6f6e407 in _g_closure_invoke_va (closure=0x643ad0, return_value=0x7fffffffdc70, instance=0x7ca1f0, args=0x7fffffffde38, n_params=1, param_types=0x643b00) at /build/buildd/glib2.0-2.34.0/./gobject/gclosure.c:840
        marshal = 0x7ffff6f6c7a0 <g_type_class_meta_marshalv>
        marshal_data = 0x188
        in_marshal = 0
        real_closure = 0x643ab0
        __PRETTY_FUNCTION__ = "_g_closure_invoke_va"
#25 0x00007ffff6f86df6 in g_signal_emit_valist (instance=0x7ca1f0, signal_id=<optimised out>, detail=0, var_args=var_args@entry=0x7fffffffde38) at /build/buildd/glib2.0-2.34.0/./gobject/gsignal.c:3211
        return_accu = <optimised out>
        accu = {g_type = 20, data = {{v_int = 0, v_uint = 0, v_long = 0, v_ulong = 0, v_int64 = 0, v_uint64 = 0, v_float = 0, v_double = 0, v_pointer = 0x0}, {v_int = 0, v_uint = 0, v_long = 0, v_ulong = 0, v_int64 = 0, v_uint64 = 0, v_float = 0, v_double = 0, v_pointer = 0x0}}}
        accumulator = 0x643980
        emission = {next = 0x0, instance = 0x7ca1f0, ihint = {signal_id = 29, detail = 0, run_type = G_SIGNAL_RUN_LAST}, state = EMISSION_RUN, chain_type = 6609024}
        signal_id = <optimised out>
        instance_type = <optimised out>
        emission_return = {g_type = 20, data = {{v_int = 0, v_uint = 0, v_long = 0, v_ulong = 0, v_int64 = 0, v_uint64 = 0, v_float = 0, v_double = 0, v_pointer = 0x0}, {v_int = 0, v_uint = 0, v_long = 0, v_ulong = 0, v_int64 = 0, v_uint64 = 0, v_float = 0, v_double = 0, v_pointer = 0x0}}}
        rtype = 20
        static_scope = 0
        closure = 0x643ad0
        run_type = <optimised out>
        hlist = 0x643980
        l = <optimised out>
        fastpath = 20
        instance_and_params = <optimised out>
        signal_return_type = <optimised out>
        param_values = <optimised out>
        node = 0x643b20
        i = <optimised out>
        n_params = <optimised out>
        __PRETTY_FUNCTION__ = "g_signal_emit_valist"
#26 0x00007ffff6f87642 in g_signal_emit (instance=<optimised out>, signal_id=<optimised out>, detail=<optimised out>) at /build/buildd/glib2.0-2.34.0/./gobject/gsignal.c:3356
        var_args = {{gp_offset = 24, fp_offset = 48, overflow_arg_area = 0x7fffffffdf10, reg_save_area = 0x7fffffffde50}}
#27 0x00007ffff79dec2e in ?? () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
No symbol table info available.
#28 0x00007ffff78ad955 in ?? () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
No symbol table info available.
#29 0x00007ffff78af653 in gtk_main_do_event () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
No symbol table info available.
#30 0x00007ffff59937d2 in ?? () from /usr/lib/x86_64-linux-gnu/libgdk-3.so.0
No symbol table info available.
#31 0x00007ffff6aacab5 in g_main_dispatch (context=0x6605e0) at /build/buildd/glib2.0-2.34.0/./glib/gmain.c:2715
        dispatch = 0x7ffff59937b0
        was_in_call = 0
        user_data = 0x0
        callback = 0x0
        cb_funcs = 0x0
        cb_data = 0x0
        current_source_link = {data = 0x689350, next = 0x0}
        need_destroy = <optimised out>
        source = 0x689350
        current = 0x6aeb20
        i = <optimised out>
#32 g_main_context_dispatch (context=context@entry=0x6605e0) at /build/buildd/glib2.0-2.34.0/./glib/gmain.c:3219
No locals.
#33 0x00007ffff6aacde8 in g_main_context_iterate (context=0x6605e0, block=block@entry=1, dispatch=dispatch@entry=1, self=<optimised out>) at /build/buildd/glib2.0-2.34.0/./glib/gmain.c:3290
        max_priority = 2147483647
        timeout = -1
        some_ready = 1
        nfds = <optimised out>
        allocated_nfds = <optimised out>
        fds = 0x85acc0
#34 0x00007ffff6aad1e2 in g_main_loop_run (loop=0x91d8d0) at /build/buildd/glib2.0-2.34.0/./glib/gmain.c:3484
        __PRETTY_FUNCTION__ = "g_main_loop_run"
#35 0x00007ffff78ae9b5 in gtk_main () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
No symbol table info available.
#36 0x0000000000409909 in ?? ()
No symbol table info available.
#37 0x00007ffff5beb76d in __libc_start_main () from /lib/x86_64-linux-gnu/libc.so.6
No symbol table info available.
#38 0x000000000040994d in ?? ()
No symbol table info available.
#39 0x00007fffffffe1f8 in ?? ()
No symbol table info available.
#40 0x000000000000001c in ?? ()
No symbol table info available.
#41 0x0000000000000001 in ?? ()
No symbol table info available.
#42 0x00007fffffffe4cf in ?? ()
No symbol table info available.
#43 0x0000000000000000 in ?? ()
No symbol table info available.
(gdb) info registers
rax            0xfffffffffffffdfc    -516
rbx            0xea60    60000
rcx            0xffffffffffffffff    -1
rdx            0xea60    60000
rsi            0x3    3
rdi            0xb4ac50    11840592
rbp            0xab9820    0xab9820
rsp            0x7fffffffcd30    0x7fffffffcd30
r8             0x0    0
r9             0xea60    60000
r10            0x0    0
r11            0x293    659
r12            0x7fffffffcdb0    140737488342448
r13            0xb4ac50    11840592
r14            0x3    3
r15            0xab98d8    11245784
rip            0x7ffff5cb2303    0x7ffff5cb2303 <poll+83>
eflags         0x293    [ CF AF SF IF ]
cs             0x33    51
ss             0x2b    43
ds             0x0    0
es             0x0    0
fs             0x0    0
gs             0x0    0
(gdb) x/16i $pc
=> 0x7ffff5cb2303 <poll+83>:    cmp    $0xfffffffffffff000,%rax
   0x7ffff5cb2309 <poll+89>:    ja     0x7ffff5cb232f <poll+127>
   0x7ffff5cb230b <poll+91>:    mov    %r8d,%edi
   0x7ffff5cb230e <poll+94>:    mov    %eax,0x18(%rsp)
   0x7ffff5cb2312 <poll+98>:    callq  0x7ffff5ccba50
   0x7ffff5cb2317 <poll+103>:    mov    0x18(%rsp),%eax
   0x7ffff5cb231b <poll+107>:    jmp    0x7ffff5cb22d0 <poll+32>
   0x7ffff5cb231d <poll+109>:    mov    0x2cfafc(%rip),%rdx        # 0x7ffff5f81e20
   0x7ffff5cb2324 <poll+116>:    neg    %eax
   0x7ffff5cb2326 <poll+118>:    mov    %eax,%fs:(%rdx)
   0x7ffff5cb2329 <poll+121>:    or     $0xffffffffffffffff,%rax
   0x7ffff5cb232d <poll+125>:    jmp    0x7ffff5cb22d0 <poll+32>
   0x7ffff5cb232f <poll+127>:    mov    0x2cfaea(%rip),%rdx        # 0x7ffff5f81e20
   0x7ffff5cb2336 <poll+134>:    neg    %eax
   0x7ffff5cb2338 <poll+136>:    mov    %eax,%fs:(%rdx)
   0x7ffff5cb233b <poll+139>:    or     $0xffffffffffffffff,%rax
(gdb) thread apply all backtrace

Thread 4 (Thread 0x7fffe5c06700 (LWP 19524)):
#0  0x00007ffff5cb2303 in poll () from /lib/x86_64-linux-gnu/libc.so.6
#1  0x00007ffff6aacd84 in g_main_context_poll (n_fds=1, fds=0x7fffd40010c0, timeout=-1, context=0x9e7fe0, priority=<optimised out>) at /build/buildd/glib2.0-2.34.0/./glib/gmain.c:3584
#2  g_main_context_iterate (context=context@entry=0x9e7fe0, block=block@entry=1, dispatch=dispatch@entry=1, self=<optimised out>) at /build/buildd/glib2.0-2.34.0/./glib/gmain.c:3285
#3  0x00007ffff6aacea4 in g_main_context_iteration (context=0x9e7fe0, may_block=1) at /build/buildd/glib2.0-2.34.0/./glib/gmain.c:3351
#4  0x00007fffe5c0d4ad in ?? () from /usr/lib/x86_64-linux-gnu/gio/modules/libdconfsettings.so
#5  0x00007ffff6ad0645 in g_thread_proxy (data=0x917b70) at /build/buildd/glib2.0-2.34.0/./glib/gthread.c:797
#6  0x00007ffff5f90e9a in start_thread () from /lib/x86_64-linux-gnu/libpthread.so.0
#7  0x00007ffff5cbdcbd in clone () from /lib/x86_64-linux-gnu/libc.so.6
#8  0x0000000000000000 in ?? ()

Thread 2 (Thread 0x7fffeea21700 (LWP 19522)):
#0  0x00007ffff5cb2303 in poll () from /lib/x86_64-linux-gnu/libc.so.6
#1  0x00007ffff6aacd84 in g_main_context_poll (n_fds=3, fds=0x7fffe80010e0, timeout=-1, context=0x664aa0, priority=<optimised out>) at /build/buildd/glib2.0-2.34.0/./glib/gmain.c:3584
#2  g_main_context_iterate (context=0x664aa0, block=block@entry=1, dispatch=dispatch@entry=1, self=<optimised out>) at /build/buildd/glib2.0-2.34.0/./glib/gmain.c:3285
#3  0x00007ffff6aad1e2 in g_main_loop_run (loop=0x6ab2b0) at /build/buildd/glib2.0-2.34.0/./glib/gmain.c:3484
#4  0x00007ffff72793b6 in gdbus_shared_thread_func (user_data=0x664a70) at /build/buildd/glib2.0-2.34.0/./gio/gdbusprivate.c:277
#5  0x00007ffff6ad0645 in g_thread_proxy (data=0x6a6d90) at /build/buildd/glib2.0-2.34.0/./glib/gthread.c:797
#6  0x00007ffff5f90e9a in start_thread () from /lib/x86_64-linux-gnu/libpthread.so.0
#7  0x00007ffff5cbdcbd in clone () from /lib/x86_64-linux-gnu/libc.so.6
#8  0x0000000000000000 in ?? ()

Thread 1 (Thread 0x7ffff7fbc940 (LWP 19513)):
#0  0x00007ffff5cb2303 in poll () from /lib/x86_64-linux-gnu/libc.so.6
#1  0x00007ffff2c47113 in ?? () from /lib/x86_64-linux-gnu/libusb-1.0.so.0
#2  0x00007ffff2c47d87 in libusb_handle_events_timeout_completed () from /lib/x86_64-linux-gnu/libusb-1.0.so.0
#3  0x00007ffff2c47e50 in libusb_handle_events_completed () from /lib/x86_64-linux-gnu/libusb-1.0.so.0
#4  0x00007ffff2c485c9 in ?? () from /lib/x86_64-linux-gnu/libusb-1.0.so.0
#5  0x00007ffff2c48994 in libusb_bulk_transfer () from /lib/x86_64-linux-gnu/libusb-1.0.so.0
#6  0x00007ffff68446b3 in ptp_write_func (size=size@entry=16, data=0xb6b9b0, written=written@entry=0x7fffffffcf18, handler=0x7fffffffcf20, handler=0x7fffffffcf20) at libusb1-glue.c:970
#7  0x00007ffff6845618 in ptp_usb_sendreq (params=0xb62730, req=0x7fffffffd2e0) at libusb1-glue.c:1160
#8  0x00007ffff6835de8 in ptp_transaction_new (handler=<optimised out>, sendlen=<optimised out>, flags=<optimised out>, ptp=0x7fffffffd2e0, params=0xb62730) at ptp.c:152
#9  ptp_transaction_new (params=0xb62730, ptp=0x7fffffffd2e0, flags=<optimised out>, sendlen=<optimised out>, handler=<optimised out>) at ptp.c:138
#10 0x00007ffff6836d5e in ptp_opensession (params=params@entry=0xb62730, session=session@entry=1) at ptp.c:541
#11 0x00007ffff6846844 in configure_usb_device (device=device@entry=0x9dd8e0, params=params@entry=0xb62730, usbinfo=usbinfo@entry=0xb4aad0) at libusb1-glue.c:1992
#12 0x00007ffff682b491 in LIBMTP_Open_Raw_Device_Uncached (rawdevice=0x9dd8e0) at libmtp.c:1860
#13 0x00007ffff682c106 in LIBMTP_Open_Raw_Device (rawdevice=<optimised out>) at libmtp.c:2077
#14 0x000000000040a02c in ?? ()
#15 0x000000000041b73b in ?? ()
#16 0x00007ffff6f6e140 in g_closure_invoke (closure=0x8c1490, return_value=0x0, n_param_values=1, param_values=0x7fffffffd730, invocation_hint=0x7fffffffd6d0) at /build/buildd/glib2.0-2.34.0/./gobject/gclosure.c:777
#17 0x00007ffff6f7f550 in signal_emit_unlocked_R (node=node@entry=0x64cd30, detail=detail@entry=0, instance=instance@entry=0x7cd000, emission_return=emission_return@entry=0x0, instance_and_params=instance_and_params@entry=0x7fffffffd730) at /build/buildd/glib2.0-2.34.0/./gobject/gsignal.c:3551
#18 0x00007ffff6f874af in g_signal_emit_valist (instance=0x7cd000, signal_id=<optimised out>, detail=0, var_args=var_args@entry=0x7fffffffd978) at /build/buildd/glib2.0-2.34.0/./gobject/gsignal.c:3300
#19 0x00007ffff6f87642 in g_signal_emit (instance=<optimised out>, signal_id=<optimised out>, detail=<optimised out>) at /build/buildd/glib2.0-2.34.0/./gobject/gsignal.c:3356
#20 0x00007ffff79de04c in gtk_widget_activate () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#21 0x00007ffff78cdbfe in gtk_menu_shell_activate_item () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#22 0x00007ffff78cdf9b in ?? () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#23 0x00007ffff78afaaf in ?? () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#24 0x00007ffff6f6e407 in _g_closure_invoke_va (closure=0x643ad0, return_value=0x7fffffffdc70, instance=0x7ca1f0, args=0x7fffffffde38, n_params=1, param_types=0x643b00) at /build/buildd/glib2.0-2.34.0/./gobject/gclosure.c:840
#25 0x00007ffff6f86df6 in g_signal_emit_valist (instance=0x7ca1f0, signal_id=<optimised out>, detail=0, var_args=var_args@entry=0x7fffffffde38) at /build/buildd/glib2.0-2.34.0/./gobject/gsignal.c:3211
#26 0x00007ffff6f87642 in g_signal_emit (instance=<optimised out>, signal_id=<optimised out>, detail=<optimised out>) at /build/buildd/glib2.0-2.34.0/./gobject/gsignal.c:3356
#27 0x00007ffff79dec2e in ?? () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#28 0x00007ffff78ad955 in ?? () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#29 0x00007ffff78af653 in gtk_main_do_event () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#30 0x00007ffff59937d2 in ?? () from /usr/lib/x86_64-linux-gnu/libgdk-3.so.0
#31 0x00007ffff6aacab5 in g_main_dispatch (context=0x6605e0) at /build/buildd/glib2.0-2.34.0/./glib/gmain.c:2715
#32 g_main_context_dispatch (context=context@entry=0x6605e0) at /build/buildd/glib2.0-2.34.0/./glib/gmain.c:3219
#33 0x00007ffff6aacde8 in g_main_context_iterate (context=0x6605e0, block=block@entry=1, dispatch=dispatch@entry=1, self=<optimised out>) at /build/buildd/glib2.0-2.34.0/./glib/gmain.c:3290
#34 0x00007ffff6aad1e2 in g_main_loop_run (loop=0x91d8d0) at /build/buildd/glib2.0-2.34.0/./glib/gmain.c:3484
#35 0x00007ffff78ae9b5 in gtk_main () from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#36 0x0000000000409909 in ?? ()
#37 0x00007ffff5beb76d in __libc_start_main () from /lib/x86_64-linux-gnu/libc.so.6
#38 0x000000000040994d in ?? ()
#39 0x00007fffffffe1f8 in ?? ()
#40 0x000000000000001c in ?? ()
#41 0x0000000000000001 in ?? ()
#42 0x00007fffffffe4cf in ?? ()
#43 0x0000000000000000 in ?? ()
(gdb) quit
A debugging session is active.

    Inferior 1 [process 19513] will be killed.

Quit anyway? (y or n) [/HTML]

---

