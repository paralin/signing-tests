# signing-tests

Prototype repo for figuring out how to install the Windows code-signing
dependencies (TrustedSigning PowerShell module, sign .NET CLI, NuGet packages)
that `Invoke-TrustedSigning` needs, without actually signing or using real
secrets.

The goal is to reproduce and fix the failure mode:

```
Invoke-TrustedSigning: Failed to install package: sign 0.9.1-beta.24469.1
```

seen in the spacewave plugin-release CI when the `TrustedSigning` 0.5.8
PowerShell module's `Get-EveryDependency` runs `dotnet tool install sign` and
the install fails (with stdout silently swallowed by the module).
