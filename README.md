# dArkOSFIXED
dArkOS Fixed is a custom firmware based on the ArkOS4Clone project, designed to provide a more stable and reliable experience for retro gaming handhelds. This fork specifically addresses critical first-boot initialization bugs that previously left devices in an unusable state.

## 🛠️ What's Fixed

The primary focus of this release is resolving the fatal partition expansion and formatting errors found in the original ArkOS4Clone base:

- **EASYROMS exFAT Formatting Bug:** Fixed a critical syntax error in the `expandtoexfat.sh` script (`mkfs.exfat` parameters). Previously, the script attempted to set an invalid physical sector size instead of the cluster size, causing the format process to crash.
- **FAT32/vfat Lockup Resolved:** Due to the formatting crash in previous builds, the EASYROMS partition would remain stuck in FAT32, breaking directory structures, failing to mount properly, and rendering the OS unusable. This is now fully resolved; the partition correctly formats to exFAT on the first boot.
- **Volume Label Correction:** Fixed invalid flags used for assigning the EASYROMS volume label, ensuring it is correctly identified by EmulationStation and PortMaster dependencies.
- **Overall First-Boot Stability:** Ensured the script properly halts and reboots the device at the correct stages without leaving orphaned configuration files.
