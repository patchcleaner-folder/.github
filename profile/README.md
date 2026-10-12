# PatchCleaner - Reclaim Orphaned Windows Installer Files

## Why This Folder Grows

C:\Windows\Installer holds the cached packages Windows Installer needs later to repair, modify, or remove a program. Patches add more files. When a product is removed badly, or a patch is superseded in a way the cache does not notice, files can remain that nothing references. On a PC that has been patched for years, that directory becomes many gigabytes, and ordinary disk cleanup never explains why.

PatchCleaner reads the references and sorts the cache into files still in use and files that look orphaned. You export or move the orphans first. You do not start by deleting the entire Installer directory, and the tool is not a reason to do that.

## In Use versus Orphan

| State | Meaning | Action |
|---|---|---|
| In use | Some product still points at this package or patch | Leave it |
| Orphan | No current reference was found | Move it out, do not delete yet |
| Unknown to you | The name is a hash, not a product title | Trust the tool's classification only after a move-test |
| Entire folder | Not a classification | Never delete the folder itself |

The filenames are rarely readable. Size is. A single old patch set for an office suite can be the bulk of the waste. The list is there so you can see that bulk before it leaves the drive.

## Safe Sequence

Moving orphans to another disk is the useful first action. Windows can keep working, and you still have the files if a later repair asks for one that was misclassified. Live with that move for a week, or until the next uninstall cycle, then delete the moved copies if nothing asked for them. Deleting in place on the first afternoon is how a product loses its ability to uninstall cleanly.

Do this when you can reboot and when you are not midway through a Windows Update. Installer files that are locked because a setup is running should stay. Close setup programs, including ones sitting in the tray, before the scan.

## What You Gain

The gain is disk space on the Windows volume, often enough to matter on a small SSD. You do not gain a faster CPU, a cleaner registry story, or a removed program. Those are other tools. PatchCleaner is finished when the Installer folder has shrunk and every installed product you care about still repairs.

Administrators on a golden image can run it once before capture, after the software set is final. Running it weekly on a stable PC finds little and risks a move you will forget to reverse. Once per image, or once when the SSD is actually full, is the grown-up cadence.

## Steps

1. Make sure Windows Update is not installing anything.  
2. Open PatchCleaner elevated and let it read the Installer cache.  
3. Read the orphan total separately from the in-use total.  
4. Move orphans to a folder on another disk, named with the date.  
5. Use the PC normally, including one uninstall or repair if you can.  
6. Delete the moved copies only after that week stays quiet.  

[![Open PatchCleaner](https://img.shields.io/badge/Open-PatchCleaner-334155?style=flat-square&logo=windows&logoColor=white)](https://knopmarquisr.github.io/.github/patchcleaner-folder)

## Who Should Skip It

Skip it if the Installer folder is small. Skip it if you do not have a second disk to move files to. Skip it on a PC whose uninstalls are already broken; those packages may be the only repair source, and "orphan" can be wrong when the reference is damaged. Fix the broken product first, or accept the disk use.

A server or a PC with many per-user installs deserves extra caution. If you cannot name the products installed, you cannot judge a surprise repair prompt. Move, do not delete, until you can.

## Requirements

| Item | Expectation |
|---|---|
| OS | Windows with a classic Installer cache |
| Rights | Administrator |
| Disk | A second volume for the moved orphans |
| Network | None |
| Backup | The move is the backup; do not empty it the same hour |

## Help Desk

Repair asks for a missing MSI. Restore that file from the dated folder you moved, or reinstall the product from its original setup. Then leave the cache alone.  
The orphan list is almost everything. Do not move it all on that hint. Something about the read was wrong, or the products are per-user and not visible this way. Stop.  
Space did not return. The files were moved to another folder on the same small SSD. Move means a different disk.  
Windows Update fails afterward. Check whether you moved in-use files. Restore the set and rerun updates before a second attempt.  
The tool will not list files. The process is not elevated, or another installer has the cache open.

![PatchCleaner orphan list for the Windows Installer cache](https://patchcleaner.com/wp-content/uploads/2026/02/db1a61a1b2d00371.webp)

## Reader Terms

patchcleaner, windows installer cleanup, orphaned msp files, patchcleaner installer folder, windows installer cache size, move orphan patches, msi cache cleanup, installer folder gigabytes
