# TEngine Development Patterns

> Auto-generated skill from repository analysis

## Overview

TEngine is a JavaScript-based game engine with C# tooling components. The codebase follows a hybrid architecture combining Unity project structure with custom UI generation tools and a sophisticated event system. The project emphasizes clean separation between runtime core systems and development tooling, with particular focus on automated code generation and build artifact management.

## Coding Conventions

### File Naming
- Use **PascalCase** for all file names
- Examples: `EventMgr.cs`, `ScriptAutoGenerator.cs`, `ScriptGeneratorSetting.cs`

### Import/Export Style
- **Mixed approach** based on context
- Unity C# files use standard `using` statements
- JavaScript modules use context-appropriate import patterns

### Commit Style
- **Freeform commits** with average 33 character length
- Focus on descriptive, concise messages
- No strict prefix requirements

### Directory Structure
```
UnityProject/Assets/
├── TEngine/Runtime/Core/          # Core engine systems
├── Editor/UIScriptGenerator/      # UI generation tools
Tools/
├── GameEventSourceGenerator/      # C# source generators
```

## Workflows

### Build Artifacts Cleanup
**Trigger:** When build outputs and temporary files need removal from version control  
**Command:** `/clean-build`

1. Update `.gitignore` with appropriate build patterns
2. Remove `bin/` and `obj/` directories from Tools projects
3. Clean up generated `.deps.json`, `.dll`, and `.pdb` files
4. Clear NuGet cache and temporary project files
5. Verify no build artifacts remain in version control

```gitignore
# Build artifacts
**/bin/
**/obj/
*.deps.json
*.dll
*.pdb
```

### UI Script Generator Improvements
**Trigger:** When enhancing UI script generation capabilities  
**Command:** `/enhance-ui-gen`

1. Modify `ScriptAutoGenerator.cs` for new component detection logic
2. Update `ScriptGenerator.cs` with enhanced generation templates
3. Configure `ScriptGeneratorSetting.cs` with new generation rules
4. Test generation workflow with new UI components
5. Validate generated scripts compile and function correctly

```csharp
// Example enhancement pattern
public class ScriptAutoGenerator
{
    // Add new component type support
    private void ProcessNewComponentType()
    {
        // Implementation for new UI component
    }
}
```

### Game Event System Development
**Trigger:** When enhancing event system functionality  
**Command:** `/update-events`

1. Update core logic in `EventMgr.cs`
2. Modify `EventInterfaceAttribute.cs` for new event patterns
3. Rebuild `SourceGenerator.dll` with latest changes
4. Deploy updated analyzer DLLs to Unity project
5. Test event generation and runtime performance

```csharp
// Event system pattern
[EventInterface]
public interface IGameEvent
{
    void Execute();
}
```

### Pull Request Integration
**Trigger:** When merging contributor pull requests  
**Command:** `/merge-pr`

1. Thoroughly review all pull request changes
2. Verify changes align with project architecture
3. Merge with main branch using appropriate strategy
4. Update any affected core system files
5. Ensure build artifacts are properly managed post-merge

### C# Tools Project Build
**Trigger:** When building GameEventSourceGenerator tools  
**Command:** `/build-tools`

1. Clean previous build outputs
2. Compile C# source generator projects
3. Generate required `.dll` assemblies
4. Create associated `.deps.json` dependency files
5. Generate `.pdb` debug symbol files
6. Update Unity project references to new tools

```bash
# Build command pattern
dotnet build Tools/GameEventSourceGenerator/
dotnet publish --output UnityProject/Assets/TEngine/Runtime/Core/GameEvent/
```

## Testing Patterns

### Test File Organization
- Test files follow `*.test.*` naming pattern
- Framework details not explicitly configured
- Tests likely integrated with Unity Test Runner for C# components
- JavaScript testing approach follows project-specific patterns

### Testing Approach
```javascript
// Assumed test pattern based on analysis
describe('ComponentName', () => {
    it('should perform expected behavior', () => {
        // Test implementation
    });
});
```

## Commands

| Command | Purpose |
|---------|---------|
| `/clean-build` | Remove build artifacts and temporary files |
| `/enhance-ui-gen` | Improve UI script generation capabilities |
| `/update-events` | Develop game event system functionality |
| `/merge-pr` | Integrate pull request changes |
| `/build-tools` | Build C# source generator tools |