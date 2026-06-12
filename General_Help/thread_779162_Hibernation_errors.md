---
title: "Hibernation errors"
date: 2008-05-02
forum: General Help
---

### Post by hair on 2008-05-02
Hello,
When I resume my kubuntu system from hibernation, it starts on console, and doesn't automatically jump to X. How do I change that?

Furthermore, I get some error messages:
Both when hibernating and when resuming: 
```
i8042 kbd 00:0b: activation failed
```
After resuming, in syslog: 
```
ACPI Error (dsopcode-0481): Attempt to CreateField of length zero [20070126]
ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SAT1.RATA] (Node f7c4bfa8), AE_AML_OPERAND_VALUE
ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SAT1.CHN0.DRV0._GTF] (Node f7c4bd20), AE_AML_OPERAND_VALUE
ata7.00: _GTF evaluation failed (AE 0x3006)
ACPI Error (dsopcode-0481): Attempt to CreateField of length zero [20070126]
ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SAT1.RATA] (Node f7c4bfa8), AE_AML_OPERAND_VALUE
ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SAT1.CHN1.DRV0._GTF] (Node f7c4be10), AE_AML_OPERAND_VALUE
ata8.00: _GTF evaluation failed (AE 0x3006)
```
Does that mean anything?

TIA.

---

