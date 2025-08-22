# nuroX Organization Default Workflows

This directory contains workflows that are automatically added to **ALL new repositories** created in the nuroX organization.

## 🎯 Purpose

Organization default workflows provide:
- ✅ **Automatic compliance enforcement** across all repositories
- ✅ **Zero-configuration setup** for developers
- ✅ **Consistent quality standards** organization-wide
- ✅ **Smart detection** to avoid interference with non-applicable repositories

## 📁 Current Default Workflows

### `auto-validate-action.yml`
**Automatic GitHub Action Validation**

- **Triggers**: Push/PR to main branches when action files change
- **Detection**: Only runs on repositories with "action" in name AND action.yml file
- **Validation**: Enforces nuroX standards for GitHub Actions including:
  - Schema validation (YAML syntax, required fields)
  - nuroX standards compliance (author, naming, description)
  - Security assessment (secrets detection, version pinning)
  - Documentation validation (README, LICENSE)
  - Security scoring (minimum 70/100)

**Auto-applied to**: All new repositories (smart detection prevents false positives)

## 🚀 How It Works

When a new repository is created in the nuroX organization:

1. **GitHub automatically adds** all workflows from this directory
2. **Smart detection logic** determines if validation should run:
   - ✅ Repository name contains "action" + action.yml exists → **Validation runs**
   - ❌ Regular repository or missing action file → **Validation skipped**
3. **Developers get immediate feedback** on compliance with nuroX standards
4. **Quality gates** prevent non-compliant code from being merged

## 📊 Impact

### Before Organization Defaults:
- ❌ Manual workflow setup required for each new repository
- ❌ Inconsistent validation across repositories
- ❌ Risk of non-compliant actions being missed

### After Organization Defaults:
- ✅ **100% automatic coverage** for new repositories
- ✅ **Consistent enforcement** across all GitHub Actions
- ✅ **Zero developer friction** - works automatically
- ✅ **Scalable governance** for unlimited repositories

## 🔧 Maintenance

### Adding New Default Workflows:
1. Add workflow file to `.github/workflows/` directory
2. Commit and push to this repository
3. All future repositories will automatically include the workflow

### Updating Existing Workflows:
1. Modify the workflow file in this directory
2. Commit and push changes
3. **Note**: Existing repositories keep their current version
4. **Recommendation**: Use deployment scripts to update existing repositories if needed

## 🧪 Testing Organization Defaults

### Test New Repository Creation:
```bash
# 1. Create test repository with "action" in name
gh repo create nuroX-global/test-org-default-validation-action --public

# 2. Verify workflow was auto-added
gh api repos/nuroX-global/test-org-default-validation-action/contents/.github/workflows/auto-validate-action.yml

# 3. Add action.yml and test validation
git clone https://github.com/nuroX-global/test-org-default-validation-action
cd test-org-default-validation-action
echo 'name: "Test Action"
description: "Testing organization defaults"
author: "nuroX Global"
runs:
  using: "composite"
  steps: []' > action.yml

git add action.yml
git commit -m "feat: add test action"
git push

# 4. Check GitHub Actions tab - validation should run automatically!
```

### Test Non-Action Repository:
```bash
# 1. Create regular repository (no "action" in name)
gh repo create nuroX-global/test-regular-library --public

# 2. Add content and push
echo "# Test Library" > README.md
git add README.md
git commit -m "feat: add readme"
git push

# 3. Workflow should be present but validation should be skipped
```

## 📈 Success Metrics

- ✅ **New action repositories**: Automatic validation from day one
- ✅ **Compliance rate**: 100% coverage for detected GitHub Actions
- ✅ **Developer satisfaction**: Zero manual setup required
- ✅ **Quality improvement**: Immediate feedback on standards compliance

---

*Part of the nuroX Global CI/CD ecosystem ensuring quality and compliance across all repositories.* 🚀
