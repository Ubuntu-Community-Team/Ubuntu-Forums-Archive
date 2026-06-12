---
title: "kworker eats 97% cpu"
date: 2016-03-07
forum: General Help
---

### Post by Roman_Steiner on 2016-03-07
Hello!


I don't really know where to find help, since this seems to be a very localized problem, google doesn't seem to very helpful. So I'll just post this here.
Since the last reboot on my laptop a kworker process eats a whole cpu core. I've tried rebooting with another kernel (3.19.0-25-generic), but that didn't help. 


Here are the things of which I think might be relevant (but I don't really know what to do with them):




```

$ uname -r
3.19.0-51-generic

$ grep . -r /sys/firmware/acpi/interrupts/
/sys/firmware/acpi/interrupts/sci: 2026780
/sys/firmware/acpi/interrupts/error:       0
/sys/firmware/acpi/interrupts/gpe00:       0   invalid
/sys/firmware/acpi/interrupts/gpe01:       0   invalid
/sys/firmware/acpi/interrupts/gpe02:       0   invalid
/sys/firmware/acpi/interrupts/gpe03:      63   enabled
/sys/firmware/acpi/interrupts/gpe04:       0   invalid
--- cut ----
/sys/firmware/acpi/interrupts/gpe4F:       0   invalid
/sys/firmware/acpi/interrupts/gpe61: 2026719   enabled
/sys/firmware/acpi/interrupts/gpe62:       0   enabled
---- cut ----
/sys/firmware/acpi/interrupts/sci_not:       0
/sys/firmware/acpi/interrupts/ff_pmtimer:       0   invalid
/sys/firmware/acpi/interrupts/ff_rt_clk:       0   disabled
/sys/firmware/acpi/interrupts/gpe_all: 2026786
/sys/firmware/acpi/interrupts/ff_gbl_lock:       0   enabled
/sys/firmware/acpi/interrupts/ff_pwr_btn:       0   enabled
/sys/firmware/acpi/interrupts/ff_slp_btn:       0   invalid

$ perf report
+   91.53%     0.00%  kworker/0:1      [kernel.kallsyms]             [k] ret_from_fork
+   91.53%     0.00%  kworker/0:1      [kernel.kallsyms]             [k] kthread
+   91.53%     0.01%  kworker/0:1      [kernel.kallsyms]             [k] worker_thread
+   91.43%     0.01%  kworker/0:1      [kernel.kallsyms]             [k] process_one_work 
+   91.41%     0.00%  kworker/0:1      [kernel.kallsyms]             [k] acpi_os_execute_deferred       
+   90.70%     0.01%  kworker/0:1      [kernel.kallsyms]             [k] acpi_ev_asynch_execute_gpe_method
+   90.62%     0.01%  kworker/0:1      [kernel.kallsyms]             [k] acpi_ns_evaluate                   
+   90.41%     0.00%  kworker/0:1      [kernel.kallsyms]             [k] acpi_ps_execute_method      
+   90.33%     0.01%  kworker/0:1      [kernel.kallsyms]             [k] acpi_ps_parse_aml            
+   89.72%     0.91%  kworker/0:1      [kernel.kallsyms]             [k] acpi_ps_parse_loop         
+   75.94%     0.37%  kworker/0:1      [kernel.kallsyms]             [k] acpi_ds_exec_end_op                 
+   67.57%     0.06%  kworker/0:1      [kernel.kallsyms]             [k] acpi_ds_evaluate_name_path       
+   62.45%     0.17%  kworker/0:1      [kernel.kallsyms]             [k] acpi_ex_resolve_to_value      
+   61.94%     0.05%  kworker/0:1      [kernel.kallsyms]             [k] acpi_ex_resolve_node_to_value 
+   61.85%     0.11%  kworker/0:1      [kernel.kallsyms]             [k] acpi_ex_read_data_from_field   
+   61.37%     0.58%  kworker/0:1      [kernel.kallsyms]             [k] acpi_ex_extract_from_field   
+   60.83%     0.06%  kworker/0:1      [kernel.kallsyms]             [k] acpi_ex_field_datum_io 
+   60.75%     0.17%  kworker/0:1      [kernel.kallsyms]             [k] acpi_ex_access_region   
+   60.54%     0.21%  kworker/0:1      [kernel.kallsyms]             [k] acpi_ev_address_space_dispatch   
+   60.25%     0.03%  kworker/0:1      [kernel.kallsyms]             [k] acpi_ex_pci_config_space_handler 
+   60.22%     0.11%  kworker/0:1      [kernel.kallsyms]             [k] acpi_os_read_pci_configuration 
+   60.11%     0.04%  kworker/0:1      [kernel.kallsyms]             [k] raw_pci_read    
+   60.05%    59.61%  kworker/0:1      [kernel.kallsyms]             [k] pci_conf1_read 
+    9.70%     0.48%  kworker/0:1      [kernel.kallsyms]             [k] acpi_ns_lookup
+    9.18%     0.55%  kworker/0:1      [kernel.kallsyms]             [k] acpi_ns_search_and_enter
+    7.55%     7.55%  kworker/0:1      [kernel.kallsyms]             [k] acpi_ns_search_one_scope 
+    6.29%     0.33%  kworker/0:1      [kernel.kallsyms]             [k] acpi_ds_create_operand         
+    5.97%     0.13%  kworker/0:1      [kernel.kallsyms]             [k] acpi_ps_get_next_namepath   
+    5.21%     0.02%  swapper          [kernel.kallsyms]             [k] cpu_startup_entry 
+    4.84%     0.00%  swapper          [kernel.kallsyms]             [k] cpuidle_enter                     
+    4.23%     0.00%  swapper          [kernel.kallsyms]             [k] x86_64_start_kernel          
+    4.23%     0.00%  swapper          [kernel.kallsyms]             [k] x86_64_start_reservations   
+    4.23%     0.00%  swapper          [kernel.kallsyms]             [k] start_kernel            
+    4.23%     0.00%  swapper          [kernel.kallsyms]             [k] rest_init                 
+    3.93%     0.00%  swapper          [kernel.kallsyms]             [k] ret_from_intr            
+    3.93%     0.00%  swapper          [kernel.kallsyms]             [k] do_IRQ                      
+    3.89%     0.00%  swapper          [kernel.kallsyms]             [k] handle_irq                     
+    3.88%     0.01%  swapper          [kernel.kallsyms]             [k] handle_fasteoi_irq                    
+    3.86%     0.00%  swapper          [kernel.kallsyms]             [k] handle_irq_event        
+    3.85%     0.00%  swapper          [kernel.kallsyms]             [k] handle_irq_event_percpu    
+    3.83%     0.00%  swapper          [kernel.kallsyms]             [k] acpi_ev_sci_xrupt_handler    
+    3.83%     0.00%  swapper          [kernel.kallsyms]             [k] acpi_irq               
+    3.48%     0.00%  swapper          [kernel.kallsyms]             [k] acpi_hw_read              
+    3.48%     0.55%  kworker/0:1      [kernel.kallsyms]             [k] acpi_ut_update_object_reference
+    3.47%     0.01%  swapper          [kernel.kallsyms]             [k] acpi_hw_read_port       
+    3.46%     3.46%  swapper          [kernel.kallsyms]             [k] acpi_os_read_port      
+    3.34%     0.01%  swapper          [kernel.kallsyms]             [k] acpi_ev_gpe_detect       
+    2.89%     0.50%  kworker/0:1      [kernel.kallsyms]             [k] acpi_ut_update_ref_count 
+    2.78%     0.20%  kworker/0:1      [kernel.kallsyms]             [k] acpi_ut_remove_reference 



```

Since it seemed like a problem related to PCI and interrupts, I've tried the boot flags suggested here: [https://help.ubuntu.com/community/DebuggingIRQProblems](https://help.ubuntu.com/community/DebuggingIRQProblems)

[FONT=courier new]noapic[/FONT]: the cpu usage goes down to a fixed 85% for kworker, instead of 97%
[FONT=courier new]pci=routeirq[/FONT]: no effect
[FONT=courier new]pc=noacpi[/FONT]: does not boot
[FONT=courier new]acpi=off[/FONT]: does not boot

then, since it's a new laptop, I've tried:
[FONT=courier new]nolapic[/FONT]: it seems to solve the problem 

what should I do? Edit grub options and just leave it with nolapic? Could that somehow degrade performance or damage the laptop? 
Is there a better way to solve that problem? 

Thanks for any pointer.

---

