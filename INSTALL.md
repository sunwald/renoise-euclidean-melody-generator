# Installation Guide for Renoise Euclidean Melody Generator

Three methods to get the script running in Renoise.

---

## **Method 1: Direct Script Editor (Fastest)**

Best for: Quick testing, one-off use.

### Steps:

1. **Open Renoise**
2. Go to: **Tools → Open Script Editor** (or Ctrl+Shift+X)
3. A new window opens with a blank text editor
4. **Copy all content** from [`euclidean_melody_generator.lua`](euclidean_melody_generator.lua)
5. **Paste** into the Script Editor
6. **Run** the script:
   - **Windows/Linux:** Ctrl + F5
   - **macOS:** Cmd + F5
7. View output in the **Script Editor console** (the text area below the code)

### Edit & Run Loop:

- Modify the `config` table at the top of the script
- Change `style`, `root_note`, `scale_name`, `density`, etc.
- Press Ctrl+F5 to regenerate the pattern
- Check the console output for note data

### To Use Generated Notes:

- Copy each line of output (or manually note down the MIDI values)
- Switch to your **Pattern Editor** in Renoise
- Insert notes manually into a track, or use Renoise's MIDI learn to automate

---

## **Method 2: Install as a Tool (Recommended for Repeat Use)**

Best for: Permanent installation, toolbar access, easier to update.

### Steps:

#### 1. Locate Your Tools Folder

**Windows:**
```
C:\Users\[Your Username]\AppData\Roaming\Renoise\V<version>\Scripts\Tools\
```
Example:
```
C:\Users\sunwald\AppData\Roaming\Renoise\V4.1.0\Scripts\Tools\
```

**macOS:**
```
~/Library/Preferences/Renoise/V<version>/Scripts/Tools/
```
Example:
```
/Users/sunwald/Library/Preferences/Renoise/V4.1.0/Scripts/Tools/
```

**Linux:**
```
~/.renoise/V<version>/Scripts/Tools/
```
Example:
```
/home/sunwald/.renoise/V4.1.0/Scripts/Tools/
```

> **Tip:** Replace `<version>` with your Renoise version (e.g., `4.1.0`, `4.2.0`).

#### 2. Create Tool Directory

Inside the `Tools/` folder, create a new directory:
```
com.sunwald.euclidean_melody_generator
```

Full path example:
```
C:\Users\sunwald\AppData\Roaming\Renoise\V4.1.0\Scripts\Tools\com.sunwald.euclidean_melody_generator\
```

#### 3. Create Manifest File

Inside the new folder, create a file named:
```
manifest.xml
```

Open it in a text editor and paste:
```xml
<?xml version="1.0" encoding="UTF-8"?>
<RenoiseScriptingTool>
  <ApiVersion>12</ApiVersion>
  <Id>com.sunwald.euclidean_melody_generator</Id>
  <Version>1.0.0</Version>
  <Author>Sunwald</Author>
  <Name>Euclidean Melody Generator</Name>
  <Description>Generate melodies using Euclidean rhythms, multiple scales, polyrhythms, and groove styles inspired by acid, techno, and Aphex Twin</Description>
  <Homepage>https://github.com/sunwald/renoise-euclidean-melody-generator</Homepage>
  <Category>Generator</Category>
  <KeyBinding></KeyBinding>
</RenoiseScriptingTool>
```

Save and close.

#### 4. Copy Script File

Copy [`euclidean_melody_generator.lua`](euclidean_melody_generator.lua) into the same directory:
```
com.sunwald.euclidean_melody_generator/euclidean_melody_generator.lua
```

Your folder should now look like:
```
com.sunwald.euclidean_melody_generator/
├── manifest.xml
└── euclidean_melody_generator.lua
```

#### 5. Restart Renoise

Close and reopen Renoise (or just restart the tool browser).

#### 6. Run the Tool

- Go to: **Tools → Euclidean Melody Generator**
- The script will run and print output to the console
- The tool appears in your toolbar for future use

---

## **Method 3: Use Renoise Scripting Terminal (Advanced)**

Best for: Command-line users, automation, batch processing.

### Steps:

1. **Ensure you have Renoise CLI tools** installed (check Renoise documentation)
2. **Navigate to script location:**
   ```bash
   cd /path/to/renoise-euclidean-melody-generator
   ```
3. **Run via Renoise Lua:**
   ```bash
   renoise --execute-script euclidean_melody_generator.lua
   ```
   Or:
   ```bash
   renoise-lua euclidean_melody_generator.lua
   ```

4. **Output** goes to stdout (your terminal)

---

## **Troubleshooting**

### "Tools folder not found"
- Make sure you're using the correct Renoise version number
- Check that `AppData` folder is visible (Windows: enable hidden files in View Options)
- On macOS, use Finder → Go → Go to Folder and paste the path

### "Script runs but nothing in pattern"
- The script generates note data **to the console only**
- To insert into a pattern:
  1. Copy the MIDI values from the console output
  2. Use Renoise's Pattern Editor to manually enter notes, or
  3. Write a follow-up tool that uses Renoise's API to auto-insert (advanced)

### "Tool doesn't appear in Tools menu after restart"
- Check `manifest.xml` for XML syntax errors
- Verify the `Id` field is unique (use `com.` prefix)
- Restart Renoise completely
- Check `Tools → System Console` for error messages

### "Script crashes or throws errors"
- Look at the error message in the Script Editor console
- Ensure Lua syntax is correct (curly braces, colons, etc.)
- Try Method 1 first to debug in isolation

---

## **Quick Customization**

Edit the `config` table in the script before running:

```lua
local config = {
  style = "acid",           -- Change to: "techno", "ambient", "aphex", "euclidean"
  root_note = 48,           -- Change to any MIDI note (0–127)
  scale_name = "dorian",    -- Change to: "major", "minor", "phrygian", etc.
  density = 64,             -- Lower = sparser notes (0–100)
  slide_prob = 28,          -- Higher = more slides (0–100)
  pattern_length = 16,      -- Longer = more steps
  -- ... customize all other params as needed
}
```

---

## **Next Steps**

- Try different **styles**: `"acid"`, `"techno"`, `"ambient"`, `"aphex"`, `"euclidean"`
- Experiment with **scales**: `"minor"`, `"dorian"`, `"phrygian"`, `"pentatonic"`, `"chromatic"`
- Adjust **density** to control how many notes appear
- Use **seed** to get reproducible patterns
- Combine multiple runs with different **root notes** for chord progressions

See [`README.md`](README.md) for full parameter guide and preset examples.

---

## **Getting Help**

- **Renoise Manual:** https://www.renoise.com/documentation
- **Lua Scripting Docs:** https://www.renoise.com/scripting
- **Issues/Questions:** Open a GitHub issue on this repository

---

**Enjoy creating experimental electronic music! 🎵**
