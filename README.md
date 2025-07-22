# ***OrganizeFolder***

**Folder Organizer Script for Gnome-Nautilus (Files)**

A smart(little-bit), safe, and user-friendly file organizer for GNOME's Nautilus file manager. Organize files by type, date, size, or prefix — with preview, undo, and logs.

**Setup**
Save the script as:
>     ~/.local/share/nautilus/scripts/OrganizeFolder

Make executable:
>     chmod +x ~/.local/share/nautilus/scripts/OrgaizeFolder

Dependency: `zenity`
Install with:
>       sudo apt install zenity

**Usage**

* Open Nautilus 📂

> Right-click on a folder

  > Go to Scripts → OrganizeFolder

   > Choose any of the following options:
    
      > 🧠 Auto-Suggest Grouping(by name prefix)
      > 🔠 Organize by File Type(by file extension)
      > 🕒 Organize by Date (by modified date)
      > 📏 Organize by Size (by size small, medium, large)
      > ↩️ Undo Last Change (uses the log timestamp to undo the last operation)
      > 📜 View Log (it shows the last changelog however all log will be saved in log folder)
>  view a preview >> confirm to organize

>  folder selection (reuse existing or create new)

>  organize📂

**Logging**

* Every `move` is logged in:
>     cd $HOME/.local/share/folder_organizer/.folder_organizer_logs
* Every `undo` operation is logged in:
>      cd $HOME/.local/share/folder_organizer/.folder_organizer_undo

**File Grouping**

* Uses `find` to list all files in current directory (not recursive)

* Groups by:   

* Filename prefix: [awk -F'[_\-]' '{print $1}']  

* Extension: awk -F. '{print $NF}'

* Modification time: date -r "$file" +%Y-%m

* File size: stat -c%s "$file"



**Tried to implement Fail Safe**
_every bit of file is importent isn't it_

* Never deletes any files

* Uses mv -n (no overwrite)

* Requires confirmation for every operation




* Full previews shown before grouping

* Skips subfolders (flat scan only(can be increased but might be unstable, so keep maxdepth=1))
