# **OGFN Arena HUD!**

This DLL will add the Arena HUD to your game, even on seasons that don't support custom pak files (14.30+)
<br>
This works on Versions S9 - S19
<br>
## **How?**
It's a pretty simple logic, every playlist has its own UIExtensions, the Arena HUD is a UIExtension but for some reason, its missing from most builds (S9+), so you can find the playlist and add that UIExtension yourself!
<br>
## **Code!**
*DLL should be injected once fully in lobby!*
<br>
*If you don't have the skills to implement this i will release a dll with it in a few days!*
<br>
*Of cource this has to be client sided and **NOT** server sided!*
```c++
void AddArenaHUDUIExtension() {
  UFortPlaylistAthena* ArenaPlaylist = UObject::FindObject<UFortPlaylistAthena>("FortPlaylistAthena Playlist_ShowdownAlt_Solo.Playlist_ShowdownAlt_Solo");
  if (!ArenaPlaylist)
    return;

  FPlaylistUIExtension NewUIExtension;
  NewUIExtension.Slot = EPlaylistUIExtensionSlot::Primary;
  /* Replace '/Game/UI/Competitive/Arena/ArenaScoringHUD.ArenaScoringHUD_C' with '/Game/UI/Frontend/Showdown/ShowdownScoringHUD.ShowdownScoringHUD_C' if you want the tournament HUD! */
  NewUIExtension.WidgetClass.ObjectID.AssetPathName = UKismetStringLibrary::Conv_StringToName("/Game/UI/Competitive/Arena/ArenaScoringHUD.ArenaScoringHUD_C");

  ArenaPlaylist->UIExtensions.Add(NewUIExtension);
}
```

