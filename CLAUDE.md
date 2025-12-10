# Nice Stamp v9.0.0 Windows - Claude Code Context

## Project Overview

Nice Stamp is a gesture-based timestamp utility. v9.0.0 adds musical chord audio feedback.

## Key Specifications

Location: `E:\My Drive\_AI\_TOTL 2025.11.2\2025.12.9 Nice Stamp v9.0.0 Specs\`

- `_Nice Stamp Core Requirements v9.0.0.md` - Core behavior, gestures, audio state machine
- `_Nice Stamp Platform Spec Windows v9.0.0.md` - Windows-specific implementation
- `Nice Stamp Musical Mapping Reference v0.1.md` - Modifier → frequency mappings

## Technology Stack

- .NET 8.0 Windows (WPF for UI)
- NAudio for audio synthesis (WASAPI)
- Low-level keyboard hooks (WH_KEYBOARD_LL)

## Audio Implementation

### Modifier → Frequency Mapping
- Ctrl = C4 (261.63 Hz) - root
- Shift = E4 (329.63 Hz) - major third  
- Alt = G4 (392.00 Hz) - perfect fifth
- Win = G3 (196.00 Hz) - low fifth

### State Machine
IDLE → BUILDING → SUSTAINED (500ms hold) → RESOLVING (C3 fade)

## Build Commands

```powershell
dotnet build
dotnet run --project NiceStamp
dotnet test NiceStamp.Tests
dotnet publish -c Release -r win-x64 --self-contained
```

## Code Style

- Follow existing v8.4.3 patterns in `_nice_stamp_v8.4.3_win`
- MVVM architecture
- Services for cross-cutting concerns
